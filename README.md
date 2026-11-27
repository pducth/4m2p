# Chia tiền nhóm

Web 1 file `index.html`, deploy bằng GitHub Pages, dữ liệu lưu bằng Firebase Realtime Database (miễn phí).

## 1. Tạo Firebase
1. Vào https://console.firebase.google.com → **Add project** (tắt Analytics cũng được).
2. Menu **Build → Realtime Database → Create database** (chọn vùng Singapore), chọn **Start in test mode**.
3. Tab **Rules**, dán rồi Publish (cho phép đọc/ghi ở nhánh `debts`, `notifs` và `days`):
   ```json
   { "rules": { "debts": { ".read": true, ".write": true }, "notifs": { ".read": true, ".write": true }, "days": { ".read": true, ".write": true } } }
   ```
4. **Project settings (⚙) → General → Your apps → Web (</>)** → đăng ký app → copy object `firebaseConfig`.
5. Mở `index.html`, dán các giá trị vào `firebaseConfig` (nhớ có `databaseURL`).

## 2. Deploy GitHub Pages
1. Tạo repo GitHub, đẩy `index.html` lên nhánh `main`.
2. **Settings → Pages → Deploy from a branch → main / root**.
3. Gửi link `https://<tên>.github.io/<repo>/` cho nhóm.

## Cách dùng
- Vào web, chọn tên mình (máy sẽ nhớ).
- **+ Chia tiền**: nhập tổng (vd `120k`), ghi chú, tick người chia (tick cả mình nếu có ăn), chia đều hoặc tự nhập từng người.
- **Tôi cần đòi**: danh sách người nợ mình, tick từng khoản khi đã nhận tiền để xoá.
- **Tôi cần trả**: các khoản mình nợ ai (chỉ xem, chủ nợ sẽ tick xoá).

Lưu ý: chưa cấu hình Firebase thì web chạy chế độ thử, chỉ lưu trên máy bạn. Rules ở trên cho phép bất kỳ ai biết link database ghi dữ liệu, chấp nhận được cho nhóm bạn thân.
