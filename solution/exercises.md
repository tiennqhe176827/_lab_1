# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, câu trả lời thường ổn định, ngắn gọn và ít thay đổi giữa các lần chạy. Khi tăng lên 0.5 hoặc 1.0, phản hồi bắt đầu đa dạng và tự nhiên hơn, có thể chọn các sự thật khác nhau hoặc diễn đạt sinh động hơn. Ở mức 1.5, câu trả lời sáng tạo hơn nhưng cũng dễ lan man hoặc kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2 đến 0.5 cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời đủ tự nhiên nhưng vẫn ưu tiên tính chính xác, ổn định và nhất quán, phù hợp với các tình huống cần hướng dẫn rõ ràng cho người dùng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Mỗi ngày có 10.000 × 3 = 30.000 lần gọi API. Với trung bình 350 token mỗi lần, tổng workload khoảng 10.500.000 token/ngày, tương đương 10.500 nhóm 1K token. Theo bảng giá trong bài, GPT-4o là $0.010/1K output token và GPT-4o-mini là $0.0006/1K output token, nên GPT-4o đắt hơn khoảng 0.010 / 0.0006 ≈ 16.7 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi tác vụ cần suy luận tốt, độ chính xác cao hoặc xử lý nội dung phức tạp, ví dụ phân tích tài liệu quan trọng, hỗ trợ ra quyết định nghiệp vụ, hoặc trả lời các câu hỏi nhiều bước. GPT-4o-mini phù hợp hơn cho các tác vụ khối lượng lớn và rủi ro thấp như chatbot FAQ, phân loại nội dung đơn giản, tóm tắt ngắn, hoặc tạo phản hồi nhanh cho các câu hỏi thường gặp.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi có thể dài hoặc người dùng cần cảm giác hệ thống đang xử lý ngay lập tức, ví dụ chatbot hội thoại, trợ lý viết nội dung, giải thích từng bước hoặc tạo báo cáo dài. Việc hiển thị từng phần giúp giảm cảm giác chờ đợi và cho phép người dùng đọc trước khi toàn bộ phản hồi hoàn tất. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý trọn vẹn trước khi hiển thị, hoặc khi ứng dụng cần parse kết quả có cấu trúc như JSON, lưu log, kiểm duyệt nội dung, hay thực hiện một hành động chỉ sau khi có toàn bộ output.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
