# VideoStar Unlock Pro Dylib

Module độc lập, tối giản chỉ phục vụ mục đích mở khóa toàn bộ tính năng Pro, VIP All-Access và chống văng app khi Sideload cho Video Star (tương thích v14.x - v15.3.3+).

## Cấu trúc thư mục
- `VideoStar_UnlockPro.m`: Mã nguồn Objective-C duy nhất (chỉ cần Foundation & UIKit, không phụ thuộc WebKit hay framework phụ).


## Chức năng chính
1. **Mở khóa VIP All-Access**:
   - Tự động kích hoạt 90 gói hiệu ứng, chuyển cảnh, bộ lọc, text anim, keyframe curve, 3D,...
   - Đặt hạn thuê bao đến năm 2100.
2. **Xóa Watermark & Triệt tiêu Popup mua gói**:
   - Vô hiệu hóa toàn bộ cờ báo `nonPurchased` trong `StoreModel`.
   - Chặn các dialog chào mua demo (`showDemoViewWithButtonImage:...`, `showUnlockableProductDialog:`).
3. **Mở khóa Preset QR Code**:
   - Bỏ qua kiểm tra bản quyền của `QRCodeManager`, cho phép quét và nhập mọi mã QR preset.
4. **Anti-Crash Sideload**:
   - Mock `CKContainer` của CloudKit để không bị crash khi sideload không có iCloud entitlement.
   - Chặn popup `"Subscription Error"` và bypass DeviceCheck.

## Cách biên dịch

### Sử dụng Xcode Clang
```bash
xcrun -sdk iphoneos clang -arch arm64 -shared -fobjc-arc \
    -framework Foundation -framework UIKit \
    -install_name @executable_path/VideoStar_UnlockPro.dylib \
    -o VideoStar_UnlockPro.dylib VideoStar_UnlockPro.m
```

### Sử dụng Make:
```bash
make
```
