# Bài tập Session 16 – Ex03: Tổ chức giao tiếp cho dự án bãi đỗ xe thông minh

Họ và tên: Thi Thành Đạt  
MSSV: N26DTCN041  
Lớp: CNTT2  
Môn học: Nhập môn Công nghệ thông tin  
Email: thithanhdat111@gmail.com

## 1. Phân tích vấn đề

Trên Messenger, thông báo về cảm biến, hạn công việc và tin nhắn giải trí nằm chung một luồng. Khi có nhiều meme hoặc câu chuyện ngoài lề, thông báo quan trọng dễ trôi khỏi màn hình. Người nhận cũng khó tìm lại đúng cuộc trao đổi để biết ai đang xử lý lỗi và hạn hoàn thành là lúc nào.

Em đề xuất chuyển trao đổi công việc sang **Slack**. Mỗi Channel dành cho một loại nội dung; mỗi vấn đề cụ thể được thảo luận bằng **Reply in thread** dưới tin nhắn mở đầu. Messenger không còn là nơi lưu quyết định và deadline của dự án.

## 2. Sơ đồ kiến trúc kênh

```text
Workspace: BaiDoXeThongMinh
├── #thong-bao
├── #ky-thuat-cam-bien
├── #tien-do-cong-viec
└── #giai-tri
```

- **#thong-bao:** Trưởng nhóm đăng deadline, thay đổi kế hoạch và quyết định đã chốt. Mỗi thông báo ghi rõ việc cần làm, người phụ trách và thời điểm hoàn thành; thông báo quan trọng được ghim để dễ tìm lại. Không đăng câu hỏi kỹ thuật hay ảnh vui ở đây.
- **#ky-thuat-cam-bien:** Đăng lỗi cảm biến, kết quả thử nghiệm và cách xử lý. Mỗi lỗi mở bằng một tin nhắn có mã/vị trí cảm biến và mô tả hiện tượng; các câu hỏi, log và tiến độ sửa được trả lời trong thread của tin đó.
- **#tien-do-cong-viec:** Mỗi thành viên cập nhật việc đã xong, việc đang làm và trở ngại. Trao đổi chi tiết về một đầu việc nằm trong thread của bản cập nhật tương ứng; khi chốt xong thì báo kết quả ngắn gọn.
- **#giai-tri:** Dành cho meme và chuyện ngoài công việc. Không chuyển thông báo deadline hoặc lỗi kỹ thuật sang kênh này.

Ví dụ, khi cảm biến ở cổng A không gửi dữ liệu, người phụ trách đăng một tin mới trong **#ky-thuat-cam-bien**. Những người cùng xử lý bấm **Reply in thread** để trao đổi bên dưới tin đó, thay vì gửi nhiều tin rời vào khung chat chính.

## 3. Ba quy tắc vàng khi giao tiếp

1. **Nhắn đủ ý ngay từ đầu, tránh No-Hello Trap.** Không chỉ nhắn “Có ai rảnh không?” rồi chờ người khác trả lời. Một tin công việc cần có bối cảnh, vấn đề, điều đã thử, người cần hỗ trợ và hạn phản hồi để người đọc có thể xử lý khi họ rảnh.
2. **Đúng kênh, đúng thread.** Tin mở đầu nêu một vấn đề; câu hỏi tiếp theo và tài liệu liên quan dùng **Reply in thread**. Chỉ đưa kết luận quan trọng ra kênh chính hoặc **#thong-bao**. Nội dung giải trí ở **#giai-tri** để thông tin kỹ thuật và deadline không bị trôi.
3. **Tag đúng người và tôn trọng thời gian tập trung.** Chỉ nhắc tên người phụ trách; không spam `@all` (trên Slack là `@channel`, `@here` hoặc `@everyone`). Người gửi ghi thời hạn cần phản hồi, không mặc định người nhận phải trả lời ngay. Thành viên đang viết code có thể tạm dừng thông báo và trả lời vào thời điểm phù hợp; việc thật sự khẩn cấp mới liên hệ trực tiếp theo quy ước của nhóm.

Như vậy, nhóm vẫn trao đổi được dù mọi người không online cùng lúc. Mỗi thành viên có thể đọc lại đúng kênh và thread, trả lời với đầy đủ ngữ cảnh, đồng thời không phải ngắt việc liên tục vì những tin nhắn không gấp.
