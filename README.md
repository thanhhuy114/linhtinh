# Cơ Sở Dữ Liệu `shop`
- Thành Viên `Võ Thành Huy`
- Thành Viên `Trần Dương Gia Thịnh`



### Bảng `products`

| Cột              | Kiểu dữ liệu    | Ý nghĩa                                                            |
|------------------|-----------------|--------------------------------------------------------------------|
| id               | BIGINT          | Khóa chính, định danh duy nhất cho mỗi sản phẩm                    |
| product_type_id  | INT             | Khóa ngoại, chỉ định loại sản phẩm                                |
| name             | VARCHAR(255)    | Tên của sản phẩm                                                   |
| price            | INT             | Giá của sản phẩm                                                   |
| url              | VARCHAR(255)    | Đường dẫn URL đến sản phẩm (nếu có)                                |
| trash            | TINYINT(1)      | Trạng thái xóa tạm thời của sản phẩm (1: đã xóa, 0: không)        |
| created_at       | DATETIME        | Ngày và giờ tạo sản phẩm                                           |
| modified_at      | DATETIME        | Ngày và giờ chỉnh sửa gần nhất của sản phẩm                       |
| deleted_at       | DATETIME        | Ngày và giờ xóa sản phẩm (nếu có)                                 |
| deleted          | TINYINT(1)      | Trạng thái xóa của sản phẩm (1: đã xóa, 0: không)                 |



### Bảng `product_types`

| Cột           | Kiểu dữ liệu | Ý nghĩa                                     |
|---------------|--------------|---------------------------------------------|
| id            | INT          | Khóa chính, định danh duy nhất cho mỗi loại sản phẩm |
| name          | VARCHAR(255) | Tên của loại sản phẩm                      |
| icon_url      | VARCHAR(255) | Đường dẫn URL đến biểu tượng loại sản phẩm |


### Bảng `stores`

| Cột             | Kiểu dữ liệu | Ý nghĩa                                     |
|-----------------|--------------|---------------------------------------------|
| id              | INT          | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| name            | VARCHAR(255) | Tên cửa hàng                               |
| phone_number    | VARCHAR(11)  | Số điện thoại của cửa hàng                 |
| manager_name    | VARCHAR(255) | Tên người quản lý cửa hàng                 |
| status          | VARCHAR(255) | Trạng thái của cửa hàng                    |
| opening_at      | DATETIME     | Ngày và giờ mở cửa hàng                   |
| province        | VARCHAR(255) | Tên tỉnh hoặc thành phố của cửa hàng      |
| district        | VARCHAR(255) | Tên quận hoặc huyện của cửa hàng          |
| ward            | VARCHAR(255) | Tên phường hoặc xã của cửa hàng           |
| details         | VARCHAR(255) | Chi tiết địa chỉ của cửa hàng             |
| additional_notes| VARCHAR(255) | Ghi chú thêm về cửa hàng                  |
| deleted         | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |


### Bảng `product_inventories`

| Cột           | Kiểu dữ liệu | Ý nghĩa                                     |
|---------------|--------------|---------------------------------------------|
| id            | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| store_id      | INT          | Khóa ngoại, chỉ định cửa hàng              |
| product_id    | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| quantity      | INT          | Số lượng tồn kho của sản phẩm              |
| modified_at   | DATETIME     | Ngày và giờ chỉnh sửa gần nhất             |


### Bảng `specifications`

| Cột             | Kiểu dữ liệu | Ý nghĩa                                     |
|-----------------|--------------|---------------------------------------------|
| id              | INT          | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| name            | VARCHAR(255) | Tên của đặc tính                          |
| note            | VARCHAR(255) | Ghi chú (nếu có)                          |
| key             | VARCHAR(255) | Khóa đặc tính                              |
| type_id         | INT          | Khóa ngoại, chỉ định loại đặc tính        |
| measure         | VARCHAR(50)  | Đơn vị đo lường của đặc tính              |
| icon_url        | VARCHAR(255) | Đường dẫn URL đến biểu tượng của đặc tính |

### Bảng `specifications_types`

| Cột             | Kiểu dữ liệu | Ý nghĩa                                     |
|-----------------|--------------|---------------------------------------------|
| id              | INT          | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| name            | VARCHAR(255) | Tên của loại đặc tính                     |
| note            | VARCHAR(255) | Ghi chú (nếu có)                          |
| icon_url        | VARCHAR(255) | Đường dẫn URL đến biểu tượng loại đặc tính |

### Bảng `product_types_specifications`

| Cột                  | Kiểu dữ liệu | Ý nghĩa                                     |
|----------------------|--------------|---------------------------------------------|
| product_types_id     | INT          | Khóa ngoại, chỉ định loại sản phẩm        |
| product_specification_id | INT      | Khóa ngoại, chỉ định đặc tính của sản phẩm |

### Bảng `products_specifications`

| Cột                  | Kiểu dữ liệu | Ý nghĩa                                     |
|----------------------|--------------|---------------------------------------------|
| id                   | INT          | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| product_id           | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| specification_id     | INT          | Khóa ngoại, chỉ định đặc tính của sản phẩm|
| info                 | VARCHAR(255) | Thông tin chi tiết về đặc tính của sản phẩm |
| created_at           | DATETIME     | Ngày và giờ tạo bản ghi                   |
| modified_at          | DATETIME     | Ngày và giờ chỉnh sửa gần nhất            |
| deleted              | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |


### Bảng `discounts`

| Cột                | Kiểu dữ liệu | Ý nghĩa                                     |
|--------------------|--------------|---------------------------------------------|
| id                 | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| product_id         | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| discount_percent   | INT          | Phần trăm giảm giá                         |
| max_product_quantity | INT        | Số lượng sản phẩm giảm giá tối đa          |
| modified_at        | DATETIME     | Ngày và giờ chỉnh sửa gần nhất             |
| started_at         | DATETIME     | Ngày bắt đầu áp dụng giảm giá              |
| ended_at           | DATETIME     | Ngày kết thúc áp dụng giảm giá             |
| deleted_at         | DATETIME     | Ngày và giờ xóa bản ghi (nếu có)          |
| deleted            | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |


### Bảng `product_ratings`

| Cột           | Kiểu dữ liệu | Ý nghĩa                                     |
|---------------|--------------|---------------------------------------------|
| id            | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| product_id    | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| comment_id    | BIGINT       | Khóa ngoại, chỉ định bình luận             |
| user_id       | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| rating        | INT          | Điểm đánh giá của sản phẩm                 |
| deleted       | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |

### Bảng `product_comments`

| Cột             | Kiểu dữ liệu | Ý nghĩa                                     |
|-----------------|--------------|---------------------------------------------|
| id              | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id         | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| parent_comment_id | BIGINT     | Khóa ngoại, chỉ định bình luận cha         |
| product_id      | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| content         | TEXT         | Nội dung bình luận                         |
| image_url       | VARCHAR(255) | Đường dẫn URL đến hình ảnh bình luận (nếu có) |
| modified_at     | DATETIME     | Ngày và giờ chỉnh sửa gần nhất             |
| is_ratinged     | TINYINT(1)   | Trạng thái đánh giá của bình luận (1: đã đánh giá, 0: chưa) |
| created_at      | DATETIME     | Ngày và giờ tạo bình luận                  |
| deleted         | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |

### Bảng `avatars`

| Cột           | Kiểu dữ liệu | Ý nghĩa                                     |
|---------------|--------------|---------------------------------------------|
| id            | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id       | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| image_url     | VARCHAR(255) | Đường dẫn URL đến hình ảnh đại diện của người dùng |
| last_modified | DATETIME     | Ngày và giờ chỉnh sửa gần nhất             |
| deleted       | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |

### Bảng `product_comments_likes`

| Cột            | Kiểu dữ liệu | Ý nghĩa                                     |
|----------------|--------------|---------------------------------------------|
| id             | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| comment_id     | BIGINT       | Khóa ngoại, chỉ định bình luận được thích  |
| user_id        | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| feeling        | TINYINT(1)   | Cảm xúc của người dùng đối với bình luận (1: thích, 0: không thích) |
| created_at     | DATETIME     | Ngày và giờ tạo bản ghi                   |
| deleted_at     | DATETIME     | Ngày và giờ xóa bản ghi (nếu có)          |

### Bảng `product_images`

| Cột            | Kiểu dữ liệu | Ý nghĩa                                     |
|----------------|--------------|---------------------------------------------|
| id             | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| product_id     | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| image_url      | VARCHAR(255) | Đường dẫn URL đến hình ảnh sản phẩm         |
| deleted        | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |



### Bảng `tokens`

| Cột         | Kiểu dữ liệu | Ý nghĩa                                     |
|-------------|--------------|---------------------------------------------|
| id          | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id     | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| token       | VARCHAR(255) | Mã thông báo (token)                        |
| login_id    | BIGINT       | Khóa ngoại, chỉ định lịch sử đăng nhập     |
| deleted     | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |

### Bảng `admins`

| Cột          | Kiểu dữ liệu | Ý nghĩa                                     |
|--------------|--------------|---------------------------------------------|
| id           | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id      | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| deleted_at   | DATETIME     | Ngày và giờ xóa bản ghi (nếu có)          |
| deleted      | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |




### Bảng `flash_sale_products`

| Cột              | Kiểu dữ liệu | Ý nghĩa                                     |
|------------------|--------------|---------------------------------------------|
| id               | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| product_id       | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| discount_percent | INT          | Phần trăm giảm giá                         |
| quantity_sale    | INT          | Số lượng sản phẩm được giảm giá            |
| flash_saled_at   | DATE         | Ngày diễn ra chương trình khuyến mãi      |
| created_at       | DATETIME     | Ngày và giờ tạo bản ghi                   |
| deleted_at       | DATETIME     | Ngày và giờ xóa bản ghi (nếu có)          |

### Bảng `product_comment_likes`

| Cột              | Kiểu dữ liệu | Ý nghĩa                                     |
|------------------|--------------|---------------------------------------------|
| id               | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| comment_id       | BIGINT       | Khóa ngoại, chỉ định bình luận             |
| user_id          | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| feeling          | TINYINT(1)   | Cảm xúc đối với bình luận (1: like, 0: dislike) |
| created_at       | DATETIME     | Ngày và giờ tạo bản ghi                   |
| deleted_at       | DATETIME     | Ngày và giờ xóa bản ghi (nếu có)          |



### Bảng `users`

| Cột               | Kiểu dữ liệu | Ý nghĩa                                     |
|-------------------|--------------|---------------------------------------------|
| id                | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| birthday          | DATE         | Ngày sinh của người dùng                    |
| gender            | TINYINT(1)   | Giới tính của người dùng (0: Nam, 1: Nữ)   |
| first_name        | VARCHAR(255) | Tên đầu tiên của người dùng                |
| middle_name       | VARCHAR(255) | Tên đệm của người dùng                     |
| last_name         | VARCHAR(255) | Họ của người dùng                          |
| password          | BIGINT       | Mật khẩu của người dùng                     |
| last_password_change| VARCHAR(255)| Ngày và giờ thay đổi mật khẩu gần nhất    |
| phone_number      | VARCHAR(255) | Số điện thoại của người dùng               |
| email             | VARCHAR(255) | Địa chỉ email của người dùng               |
| default_address_id| BIGINT       | Khóa ngoại, chỉ định địa chỉ mặc định của người dùng |
| register_at       | DATETIME     | Ngày và giờ đăng ký tài khoản              |
| blocked           | TINYINT(1)   | Trạng thái khóa của tài khoản (1: đã khóa, 0: không) |
| deleted           | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |


### Bảng `addresses`

| Cột             | Kiểu dữ liệu | Ý nghĩa                                     |
|-----------------|--------------|---------------------------------------------|
| id              | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id         | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| full_name       | VARCHAR(255) | Họ và tên đầy đủ của người nhận           |
| phone_number    | VARCHAR(255) | Số điện thoại liên hệ                     |
| province        | VARCHAR(255) | Tên tỉnh hoặc thành phố                   |
| district        | VARCHAR(255) | Tên quận hoặc huyện                       |
| ward            | VARCHAR(255) | Tên phường hoặc xã                        |
| details         | VARCHAR(255) | Địa chỉ chi tiết, số nhà, tên đường,...    |
| additional_notes| VARCHAR(255) | Ghi chú thêm (nếu có)                     |
| deleted         | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |

### Bảng `notifications`

| Cột             | Kiểu dữ liệu | Ý nghĩa                                     |
|-----------------|--------------|---------------------------------------------|
| id              | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id         | BIGINT       | Khóa ngoại, chỉ định người dùng            |
| created_at      | DATETIME     | Ngày và giờ tạo thông báo                  |
| title           | VARCHAR(255) | Tiêu đề thông báo                          |
| content         | TEXT         | Nội dung thông báo                         |
| image_url       | VARCHAR(255) | Đường dẫn URL đến hình ảnh kèm theo (nếu có) |
| read            | TINYINT(1)   | Trạng thái đã đọc của thông báo (1: đã đọc, 0: chưa) |
| deleted         | TINYINT(1)   | Trạng thái xóa của bản ghi (1: đã xóa, 0: không) |
| update_at       | DATETIME     | Ngày và giờ cập nhật thông báo (nếu có)    |

### Bảng `flash_sale_products`

| Cột               | Kiểu dữ liệu | Ý nghĩa                                     |
|-------------------|--------------|---------------------------------------------|
| id                | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| product_id        | BIGINT       | Khóa ngoại, chỉ định sản phẩm              |
| discount_percent  | INT          | Phần trăm giảm giá trong chương trình khuyến mãi |
| quantity_sale     | INT          | Số lượng sản phẩm được bán trong chương trình khuyến mãi |
| flash_saled_at    | DATE         | Ngày bắt đầu chương trình khuyến mãi       |
| created_at        | DATETIME     | Ngày và giờ tạo bản ghi                   |
| deleted_at        | DATETIME     | Ngày và giờ xóa bản ghi (nếu có)          |

### Bảng `login_history`

| Cột           | Kiểu dữ liệu | Ý nghĩa                                     |
|---------------|--------------|---------------------------------------------|
| id            | BIGINT       | Khóa chính, định danh duy nhất cho mỗi bản ghi |
| user_id       | BIGINT       | Khóa ngoại, chỉ định người dùng đăng nhập  |
| login_at      | DATETIME     | Thời gian đăng nhập                         |
| login_success | TINYINT(1)   | Trạng thái đăng nhập (1: thành công, 0: không thành công) |
| device_id     | VARCHAR(255) | ID của thiết bị                             |
| device_model  | VARCHAR(255) | Mô hình thiết bị                            |
| device_version| VARCHAR(255) | Phiên bản thiết bị                          |
