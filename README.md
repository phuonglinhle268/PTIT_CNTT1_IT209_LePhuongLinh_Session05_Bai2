Bài 2: Tái cấu trúc lịch sử commit bằng Interactive Rebase

1. Quá trình thực hiện chi tiết

Bước 1: Khởi tạo 4 commit ban đầu

Tạo lịch sử commit giả lập trên nhánh làm việc với 4 commit:

7009d9b - feat: khoi tao module auth

7139293 - fix typo

d69af64 - adds utility functions

f9f8db9 - add temp file for debug (chứa file temp.txt)

Lịch sử ban đầu qua lệnh git log --oneline:

f9f8db9 (HEAD -> master) add temp file for debug
d69af64 adds utility functions
7139293 fix typo
7009d9b feat: khoi tao module auth


Bước 2: Kích hoạt Interactive Rebase

Do cần can thiệp từ commit đầu tiên (root commit), lệnh rebase được thực thi:

git rebase -i --root


Trong trình soạn thảo Vim mở ra, tiến hành cấu hình:

Giữ nguyên commit đầu tiên (pick).

Gộp 2 commit tiếp theo vào commit đầu (squash).

Loại bỏ hoàn toàn commit rác cuối cùng (drop).

Cấu hình chi tiết:

pick 7009d9b feat: khoi tao module auth
squash 7139293 fix typo
squash d69af64 adds utility functions
drop f9f8db9 add temp file for debug


Bước 3: Đổi thông điệp commit gộp

Sau khi lưu cấu hình, Git mở trình soạn thảo thông điệp tổng hợp. Tiến hành xóa các thông điệp commit con và cập nhật thành thông điệp chuẩn theo yêu cầu:

feat: hoan thien module authentication

2. Kết quả đạt được

Lịch sử nhánh làm việc được làm sạch, không còn các commit rác (fix typo, temp file).

Toàn bộ thay đổi mã nguồn của module authentication được cô đọng trong duy nhất 1 commit sạch sẽ:

<commit_hash> feat: hoan thien module authentication


File tạm thời temp.txt không còn tồn tại trong cả cây thư mục lẫn lịch sử Git.
