# Ứng dụng chat real time bằng ngôn ngữ C
[![Open Source Love](https://img.shields.io/badge/Open%20Source-%E2%9D%A4-red.svg)](https://github.com/pranavdheer/Real-time-chat-application-in-c)
[![Build Status](https://travis-ci.org/forksociety/PyBeacon.svg?branch=master)](https://github.com/pranavdheer/Real-time-chat-application-in-c)

Sử dụng lập trình Socket và đa luồng để tạo real-time chatroom bằng ngôn ngữ C 

## Note-: 

1. Đoạn mã trên được kiểm tra cho Linux, nó sẽ hoạt động với MAC-OS và Windows nhưng chưa được kiểm tra. 
2. Code Server và Client có thể nằm trên cùng một máy cục bộ hoặc trên các máy khác nhau. Nếu bạn muốn chạy đoạn code trên máy khác, hãy đảm bảo rằng bạn có địa chỉ IP công cộng và các quyền cấp máy phù hợp (kết nối từ xa) cho máy mà bạn chạy code Server.
3. Bạn có thể chạy nhiều client để test.

### Sử dụng đoạn script Server 
```bash
./server ## script sẽ chạy trên cổng 80 by default
./server 90 ## chạy đoạn script trên cổng 90
```
### Sử dụng đoạn script Client 
```bash
./client [-h] [-a] [-p] [-u]
 -h           show guide này và thoát [optional]
 -a           IP address của server [localhost nếu chạy trên local machine] [required]
 -p           port number của server [required]
 -u           username của ngưởi dùng [required]
```
### Chức năng chatroom


| Command       | Parameter             | Desription                                 |
| ------------- | --------------------- | -------------------------------------------|
| quit          |                       | Thoát chatroom                             |
| msg           |  "text"               | Gửi tin tới tất cả online users (use"")    |
| msg           |  "text" user          | Gửi tin tới một user nhất định             |
| online        |                       | Get username của tất cả users online       |
| help          |                       | Show guide này                             |


### Server
Mỗi người dùng được xử lý bởi một thread riêng biệt trong máy chủ. Các thread đồng bộ hóa quyền truy cập vào danh sách liên kết chung
lưu trữ thông tin người dùng

### Client
Khi Client kết nối với Server, nó sẽ tạo 1 chatroom. Mỗi Client có 2 luồng đang chạy, một để gửi lệnh và luồng kia để nhận tin nhắn, cả hai đều hoạt động đồng bộ với nhau.

### TO DO 
1. Tạo môi trường thử nghiệm để kiểm tra các lỗi đồng bộ hóa
2. Sửa cùng user-name conflicts
3. Thêm feature để thay đổi user name
4. BUGS-: + Khi user đang nhập và đồng thời nhận được một tin nhắn trong phòng trò chuyện
          + Khi user gửi tin nhắn đến tất cả mọi người

## Package
sudo apt-get install libpthread-stubs0-dev
## Compile 
gcc -pthread -o term term.c
