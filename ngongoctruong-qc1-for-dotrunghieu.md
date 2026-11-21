# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): dotrunghieu  
Người kiểm (học viên): ngongoctruong  
Ngày: 2026-11-21                 Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): front_1.zip, fisheye_1.zip (không có manifest kèm theo, revision: không rõ)  
Số ảnh kiểm: 6 (+ __ ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 248 (168 shape + 80 tag)  

> Phạm vi: 20 ảnh bắt buộc (A01–A12, B01–B08); ảnh extra không kiểm. Cách kiểm: chạy `road_check lint` trên hai file, rồi phủ nhãn lên ảnh gốc từng ảnh để xem; màu vạch được đo thêm bằng pixel dọc polyline.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 20 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 24 | 0 (5 chờ lead) | nặng |
| QC1-03 position | sai thuộc tính / thừa | 39 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 39 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 39 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 39 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 57 | 0 (2 chờ lead) | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 37 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 72 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 35 | 1 | chính / nhẹ |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 56 | 0 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-10 | A10 | traffic_sign, #7 (box ≈ 25×7 px, góc (423,192)) | nhẹ | Box cao 7 px, dưới ngưỡng 8 px; lint cũng báo. Không bắt buộc gán. |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05 | Thiếu L1 và R1 (lint QC1-02). Ảnh đường hẻm đỗ xe hai bên, tôi không thấy vạch sơn nào. Có miễn lỗi không? | |
| A06 | Thiếu R1. Bên phải làn đi có vạch sơn nào không (đường dưới cầu vượt, có dải phân cách)? | |
| A09 | Thiếu R1. Bên phải làn đi là lề đường, tôi không thấy vạch. Có miễn lỗi không? | |
| A12 | Thiếu R1. Bên phải L1 có vạch hay chỉ có xe đỗ? | |
| B01, B02 | `drivable` chỉ phủ đúng vạch qua đường (hầu như trùng polygon crosswalk) và không phủ mặt đường phía xa. Với fisheye, phần đường phía sau vạch qua đường có phải thuộc `drivable` không? | |

## Quyết định
Lỗi nặng: 0 (5 mục QC1-02 chờ lead)   Lỗi chính: 0 / 248 nhãn = 0 % (2 mục QC1-07 chờ lead)   Lỗi nhẹ: 1   Ca chờ lead: 7  
Quyết định (Release / Hold / Rework): **Hold**  
Lý do (theo luật của phiếu): Chưa có lỗi nặng nào được xác nhận và tỉ lệ lỗi chính là 0 %, nên chưa phải Rework. Nhưng còn 7 ca mơ hồ chưa có lời đáp của lead (5 mục thiếu L1/R1, 2 mục vùng lái B01/B02). Theo luật, còn ca mơ hồ chưa trả lời thì Hold. Nếu lead xác nhận A05, A06, A09, A12 đúng là không có vạch và B01/B02 chấp nhận được, quyết định chuyển thành Release.
