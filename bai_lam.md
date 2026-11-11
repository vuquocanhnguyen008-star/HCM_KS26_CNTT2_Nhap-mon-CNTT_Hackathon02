# BÀI LÀM – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:** Nguyễn Vũ Quốc Anh
- **Lớp:** HCM_KS26_CNTT2
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
# Ghi lần lượt các lệnh đã chạy, mỗi lệnh một dòng
pwd
ls -Force
mv .\noi_quy_thanh_vien.txt .\docs\
mkdir backup
cp '.\data\thue_cho_thang 9.xlsx' .\backup\
rm *.tmp
cd .\logs\
ls -Force
cd ..
ls -Force -Recurse
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
 Directory: D:\starter-kit\coworking-website


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
d-----        11/11/2026   1:40 PM                backup                                                                                                      
d-----        11/11/2026   1:35 PM                data                                                                                                        
d-----        11/11/2026   1:39 PM                docs                                                                                                        
d-----        11/11/2026   1:32 PM                evidence                                                                                                    
d-----        11/11/2026   1:35 PM                logs                                                                                                        
d-----        11/11/2026   1:31 PM                web                                                                                                         
------         11/3/2026   7:08 AM             72 .env                                                                                                        
-a----         11/3/2026   7:08 AM           2409 bai_lam.md                                                                                                  


    Directory: D:\starter-kit\coworking-website\backup


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
-a----         11/3/2026   7:08 AM           6162 thue_cho_thang 9.xlsx                                                                                       


    Directory: D:\starter-kit\coworking-website\data


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
-a----         11/3/2026   7:08 AM           6162 thue_cho_thang 9.xlsx                                                                                       


    Directory: D:\starter-kit\coworking-website\docs


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
-a----         11/3/2026   7:08 AM            146 noi_quy_thanh_vien.txt                                                                                      


    Directory: D:\starter-kit\coworking-website\logs


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
-a----         11/3/2026   7:08 AM            991 member.log                                                                                                  


    Directory: D:\starter-kit\coworking-website\web


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
d-----        11/11/2026   1:31 PM                images                                                                                                      
------         11/3/2026   7:08 AM            605 app.js                                                                                                      
------         11/3/2026   7:08 AM            543 index.html                                                                                                  
------         11/3/2026   7:08 AM            460 style.css                                                                                                   


    Directory: D:\starter-kit\coworking-website\web\images


Mode                 LastWriteTime         Length Name                                                                                                        
----                 -------------         ------ ----                                                                                                        
------         11/3/2026   7:08 AM           3069 logo-coworkhub.png    

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Select-String "status=500" .\logs\member.log > .\logs\loi_500.txt
```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\member.log:3:2026-09-28 08:10:39 POST /api/dat-cho status=500
logs\member.log:4:2026-09-28 08:12:50 POST /api/dat-cho status=500
```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\member.log | Select-String "status=404").count  

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
# Ghi lệnh vào đây 
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1
```

### Nội dung file logs/tong_hop.txt

```text
==== BAO CAO SU CO WEBSITE ===

2026-09-28 08:28:45 GET /images/phong-hop-3.jpg status=404
2026-09-28 08:41:40 GET /goi-cu status=404
2026-09-28 08:49:13 GET /images/phong-hop-3.jpg status=404
2026-09-28 08:59:46 GET /images/phong-hop-3.jpg status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Network | Failed to load resource: net::ERR_FILE_NOT_FOUND | Sửa dòng 10 của file index.html thành  <img src="images/logo-coworkhub.png" alt="Logo" class="logo"> |
| 2 | Console | app.js:18 Uncaught ReferenceError: hienThiBangThue is not defined | Sửa dòng 18 của file app.js thành hienThiGoiThue(); |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Em sử dụng hệ điều hành Windows, vô file web index.html trên trình duyệt Chrome nhưng không thấy nội dung của các cột Mã gói, Gói thuê, Giá/ngày (VND)
- **Expected:** Hiển thị các nội dung của các cột 
Mã gói, Gói thuê, Giá/ngày (VND)
- **Actual:** Không hiển thị các nội dung của các cột 
Mã gói, Gói thuê, Giá/ngày (VND)
- **Log:** app.js:18 Uncaught ReferenceError: hienThiBangThue is not defined 

### Câu tìm kiếm Google

```text
site: stackoverflow.com "app.js:18 Uncaught ReferenceError: hienThiBangThue is not defined"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/thue_cho_thang_9.xlsx`, không cần ghi vào đây.
