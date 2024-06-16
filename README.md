Tên bài toán: Quản lý hệ thống thư viện
Họ tên : Triệu Văn Hiếu
MSSV : K215480106095
Email : K215480106095@tnut.edu.vn
Mô tả bài toán

Các chức năng
Quản lý người dùng:

Đăng nhập
Liệt kê tất cả người dùng
Thêm người dùng
Xóa người dùng
Đổi thông tin người dùng
Đổi mật khẩu người dùng
Kiểm tra đăng nhập
Quản lý sách:

Liệt kê tất cả sách
Thêm sách
Xóa sách
Sửa thông tin sách
Quản lý mượn trả:

Thêm phiếu mượn
Sửa phiếu mượn
Xóa phiếu mượn
Thêm chi tiết phiếu mượn
Cập nhật số lượng chi tiết phiếu mượn
Xóa dòng chi tiết phiếu mượn
Báo cáo
Báo cáo sách tồn kho
Báo cáo nhân viên cho mượn nhiều sách trong tháng
Báo cáo sách được mượn nhiều nhất trong tháng
3.1 Các bảng của hệ thống
NguoiDung

maNguoiDung (PK): INT, NOT NULL, AUTO_INCREMENT
ten: NVARCHAR(100), NOT NULL
email: NVARCHAR(100), NOT NULL, UNIQUE
soDienThoai: NVARCHAR(15), NOT NULL
diaChi: NVARCHAR(255), NULL
loaiThanhVien: NVARCHAR(50), NOT NULL
matKhau: NVARCHAR(255), NOT NULL
Sach

maSach (PK): INT, NOT NULL, AUTO_INCREMENT
tuaSach: NVARCHAR(255), NOT NULL
tacGia: NVARCHAR(255), NOT NULL
isbn: NVARCHAR(20), NOT NULL, UNIQUE
theLoai: NVARCHAR(100), NOT NULL
tongSoBan: INT, NOT NULL CHECK (tongSoBan >= 0)
soBanCoSan: INT, NOT NULL CHECK (soBanCoSan >= 0)
PhieuMuon

maPhieuMuon (PK): INT, NOT NULL, AUTO_INCREMENT
maNguoiDung (FK): INT, NOT NULL, FOREIGN KEY (maNguoiDung) REFERENCES NguoiDung(maNguoiDung)
maSach (FK): INT, NOT NULL, FOREIGN KEY (maSach) REFERENCES Sach(maSach)
ngayMuon: DATE, NOT NULL
ngayHanTra: DATE, NOT NULL
ngayTra: DATE, NULL
DatCho

maDatCho (PK): INT, NOT NULL, AUTO_INCREMENT
maNguoiDung (FK): INT, NOT NULL, FOREIGN KEY (maNguoiDung) REFERENCES NguoiDung(maNguoiDung)
maSach (FK): INT, NOT NULL, FOREIGN KEY (maSach) REFERENCES Sach(maSach)
ngayDatCho: DATE, NOT NULL
trangThai: NVARCHAR(50), NOT NULL
Phat

maPhat (PK): INT, NOT NULL, AUTO_INCREMENT
maNguoiDung (FK): INT, NOT NULL, FOREIGN KEY (maNguoiDung) REFERENCES NguoiDung(maNguoiDung)
soTien: DECIMAL(10, 2), NOT NULL CHECK (soTien > 0)
moTa: NVARCHAR(255), NULL
daThanhToan: BIT, NOT NULL DEFAULT 0
Mô tả các bảng

maNguoiDung: Mã người dùng, là khóa chính (PK).
ten: Tên người dùng, không được để trống.
email: Email của người dùng, không được để trống và phải là duy nhất.
soDienThoai: Số điện thoại của người dùng, không được để trống.
diaChi: Địa chỉ của người dùng, có thể để trống.
loaiThanhVien: Loại thành viên, không được để trống.
matKhau: Mật khẩu của người dùng, không được để trống.

maSach: Mã sách, là khóa chính (PK).
tuaSach: Tựa sách, không được để trống.
tacGia: Tác giả của sách, không được để trống.
isbn: Số ISBN của sách, không được để trống và phải là duy nhất.
theLoai: Thể loại sách, không được để trống.
tongSoBan: Tổng số bản sao của sách, phải lớn hơn hoặc bằng 0.
soBanCoSan: Số bản sao có sẵn của sách, phải lớn hơn hoặc bằng 0.

maPhieuMuon: Mã phiếu mượn, là khóa chính (PK).
maNguoiDung: Mã người dùng, là khóa ngoại (FK).
maSach: Mã sách, là khóa ngoại (FK).
ngayMuon: Ngày mượn sách, không được để trống.
ngayHanTra: Ngày hạn trả sách, không được để trống.
ngayTra: Ngày trả sách, có thể để trống.

maDatCho: Mã đặt chỗ, là khóa chính (PK).
maNguoiDung: Mã người dùng, là khóa ngoại (FK).
maSach: Mã sách, là khóa ngoại (FK).
ngayDatCho: Ngày đặt chỗ, không được để trống.
trangThai: Trạng thái đặt chỗ, không được để trống.

maPhat: Mã phạt, là khóa chính (PK).
maNguoiDung: Mã người dùng, là khóa ngoại (FK).
soTien: Số tiền phạt, phải lớn hơn 0.
moTa: Mô tả phạt, có thể để trống.
daThanhToan: Trạng thái đã thanh toán, không được để trống và mặc định là 0.
