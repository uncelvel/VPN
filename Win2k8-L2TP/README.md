# Cài đặt VPN L2TP trên Windows2k8

## Chuẩn bị môi trường

Yêu cầu: 

- Chuẩn bị OS: Windows Server 2k8 32 bit hoặc 64 bit

![](images/2k8_001.png)

![](images/2k8_002.png)

- Máy phải có 2 card mạng

![](images/2k8_000.png)

Mô hình cài đặt kết nối

## Cài đặt Routing và Remote Access Services

Click `Start` --> `Administrative Tools` --> `Server Manager`

![](images/2k8_003.png)

Trong `Server Manager` --> `Roles` --> `Roles Summary` --> `Add Roles`

![](images/2k8_004.png)

Trong màn `Before You Begin` chọn `Next`

![](images/2k8_005.png)

Trong màn `Select Server Roles` chọn `Network Policy and Access Services` và chọn `Next`

![](images/2k8_006.png)

Chọn `Next` tại màn `Network Policy and Access Services`

![](images/2k8_007.png)

Đối với màn `Select Role Services` chúng ta chọn `Routing and Remote Access Services` và chọn `Next`

![](images/2k8_008.png)

Confirm quá trình cài đặt và chọn `Next`

![](images/2k8_009.png)

Quá trình cài đặt diễn ra 

![](images/2k8_010.png)

Hoàn tất cài đặt 

![](images/2k8_011.png)

## Enable Routing and Remote Access Service

Truy cập màn `Server Manager` mở `Network Policy and Access Services` -->  Chuột phải `Routing and Remote Access` --> Chọn `Configure and Enable Routing and Remote Access`

![](images/2k8_012.png)

Bắt đầu cấu hình chọn `Next`

![](images/2k8_013.png)

Chọn `Remote access (dial-up or VPN)` và chọn `Next`

![](images/2k8_014.png)

Ở màn `Remote Access` chọn `VPN` và chọn `Next`

![](images/2k8_015.png)

Nếu chỉ có một card mạng sẽ có thông báo như sau

![](images/2k8_016.png)

Tiến hành cấu hình thêm card mạng thứ 2 và cấu hình lại 

Ở mục `VPN Connection` chọn card có kết nối Internet + Bỏ tick `Enable security ..` --> Chọn `Next`

![](images/2k8_017.png)

Cấu hình Range DHCP bằng tay 

![](images/2k8_018.png)

Chọn `New...` để tạo mới dải DHCP

![](images/2k8_019.png)

Nhập thông tin Pool DHCP cần cấp

![](images/2k8_020.png)

Chọn `Next`

![](images/2k8_021.png)

Chọn sử dụng `Routing and Remote Access` để xác thực 

![](images/2k8_022.png)

Hoàn tất cài đặt 

![](images/2k8_023.png)

Chờ thông tin cấu hình hoàn tất 

![](images/2k8_024.png)

## Remote Authentication and Forwarding options


Bây giờ chúng ta cần đặt một khóa chia sẻ trước (PSK)để tránh các tấn công kiểu ‘Man in Middle Middle (MitM).Nếu bạn muốn sử dụng xác thực chứng chỉ, bạn phải mua chứng chỉ SSL hoặc sử dụng vai trò Dịch vụ chứng chỉ Active Directory để tạo chứng chỉ của riêng bạn.

Chuột phải vào `Routing and Remote Access`

![](images/2k8_025.png)

Trong tab `General` chọn `IPv4 router` và `IPv4 Remote Access Server`

![](images/2k8_026.png)

Tại tab `IPv4` check `Enable IPv4 Forwarding`

![](images/2k8_027.png)

Tại tab `Security` check `Allow custom IPsec policy for L2TP connection` và nhập 1 chuỗi preshared key bất kỳ

![](images/2k8_028.png)

Confirm quá trình setup 

![](images/2k8_029.png)

![](images/2k8_030.png)

Để apply các setting cần restart server 

## Cấu hình Remote Access Network Policy

Mở `Server Manager` --> `Configuration` --> `Local Users and Groups` --> `Users` 

Lựa chọn User chúng ta muốn gán quyền và thực hiện click chuột phải chọn `Properties`

![](images/2k8_031.png)

Tại tab `Dial-in` chọn `Allow access` --> `Apply`

![](images/2k8_032.png)

![](images/2k8_033.png)

## Cấu hình NAT 

Trong `Server Manager` tab `Roles` --> `Network Policy and Access Services` --> `Routing And Remote Access`

Trong tab IPv4 chuột phải vào `General` --> chọn `New Routing Protocol`

![](images/2k8_034.png)

Lựa chọn `NAT` và `OK` quá trình cài đặt hoàn tất 

![](images/2k8_035.png)

## Kết nối Client Windows

Win10 chọn `Open Network & Internet settings`

![](images/2k8_036.png)

Chọn `VPN`

![](images/2k8_037.png)

Chọn `Add a VPN connection`

![](images/2k8_038.png)

Bổ sung thêm thông tin kết nối

![](images/2k8_039.png)

Chọn `Connect`

![](images/2k8_040.png)

Chờ thông tin kết nối 

![](images/2k8_041.png)

Kết nối thành công 

![](images/2k8_042.png)

Kiểm tra kết nối 

![](images/2k8_043.png)


## Kết nối Client Linux 

![](images/2k8_044.png)

![](images/2k8_045.png)

![](images/2k8_046.png)

![](images/2k8_047.png)

![](images/2k8_048.png)

![](images/2k8_049.png)

# Tài liệu tham khảo 

https://site.elastichosts.com/blog/windows-l2tpipsec-vpn-server/

https://site.elastichosts.com/blog/windows-l2tpipsec-vpn-client/

