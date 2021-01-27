# CÁC LÝ THUYẾT CƠ BẢN: MÔN CÁC GIAO THỨC MẬT MÃ (CRYPTOGRAPHIC PROTOCOLS)
*Giao thức mật mã là các giao thức nhằm thực hiện các chức năng liên quan tới bảo mật bằng các kỹ thuật mật mã. Giao thức mật mã được sử dụng rộng rãi cho việc truyền dữ liệu an toàn ở mức ứng dụng. Một giao thức mật mã tiêu biểu thường bao gồm các chức năng sau:*  
+Thỏa thuận khóa;  
+Nhận thực các bên tham gia;  
+Truyền dữ liệu an toàn;  
+Đảm bảo tính chất không thể từ chối (non-reputation).   
Các giao thức mật mã có thể được kiểm tra độ chính xác bằng các phương pháp thuần túy lý thuyết (formal verification).  
**Crypto Service Provider (CSP)** - một bộ mã chương trình logic cho các thuật toán mật mã, được triển khai trong một tệp thư viện liên kết động và cho phép các chương trình gọi các hàm chuyển đổi dữ liệu mật mã và lấy kết quả của chúng.  
**Context** - một phiên thiết lập tương tác (liên lạc) giữa server của cryptoprovider CSP và phần mềm máy tính - client trong phạm vi kiến trúc CryptoAPI.  
**Context handle** - Bộ mô tả ngữ cảnh được sử dụng để truy cập tài nguyên dịch vụ của nhà cung cấp mật mã chỉ thông qua các mô-đun trung gian của hệ điều hành, tức là không thể truy cập trực tiếp.  
**Khóa container** - cấu trúc dữ liệu để lưu giữ thông tin khóa.  
**Khóa phiên** - chuỗi kỹ thuật số, dạng động ngẫu nhiên được thiết lập trên cơ sở thông tin, được lưu trữ trong khóa container của user và biểu thị để mã hóa dữ liệu trong quá trình diễn ra phiên.  
**Khóa trao đổi** - cặp khóa thương lượng (1 công khai - public và 1 bí mật - secret), mà được dùng để mã hóa/giải mã các khóa phiên của mã hóa đối xứng để đảm bảo tương tác truyền tin an toàn đến bên tiếp nhận.  
**Khóa chữ ký** - cặp khóa chữ ký số điện tử (chữ ký- bí mật, kiểm tra chữ ký -  công khai), mà được dùng để tạo ra chữ ký số của đối tượng cần ký, và kiểm tra độ chính xác của đối tượng tiếp nhận đang nắm giữ khóa công khai.  
**CryptoAPI** -  là một giao diện lập trình ứng dụng cung cấp cho các nhà phát triển ứng dụng Windows một bộ chức năng tiêu chuẩn để làm việc với một nhà cung cấp mật mã . Một phần của hệ điều hành Microsoft. Hầu hết các tính năng CryptoAPI được hỗ trợ kể từ Windows 2000 .

CryptoAPI hỗ trợ làm việc với các khóa đối xứng và bất đối xứng , tức là nó cho phép bạn mã hóa và giải mã dữ liệu, cũng như làm việc với các chứng chỉ điện tử . Tập hợp các thuật toán mật mã được hỗ trợ phụ thuộc vào nhà cung cấp mật mã cụ thể .
# Mục đích của project 
Project yêu cầu phát triển một công cụ (chương trình) phần mềm an toàn cho phép, phù hợp với dữ liệu ban đầu cho thiết kế, triển khai các thuật toán và chức năng mật mã khác nhau để bảo vệ thông tin của người dùng hệ điều hành Linux và Windows, bao gồm cả trong quá trình kết nối mạng . Các thuật toán mật mã chính trong project này chủ yếu về biến đổi mật mã: thuật toán mã hóa, thuật toán băm, thuật toán chữ ký số điện tử (EDS). Để thực hiện các chuyển đổi mật mã trong chương trình, sử dụng các CSP được chứng nhận trên thế giới (ở phạm vi bài này tôi dùng: CryptoAPI Next Generation). Công cụ phần mềm được triển khai bằng một trong các ngôn ngữ lập trình bậc cao: С++ Builder, MS Visual C ++, C# .Net hoặc Java.  
Yêu cầu chính của project:  
1. Nắm rõ lý thuyết của các materials theo khả năng và phương án ứng dụng CSP và các giao diện ứng dụng CryptoAPI trong OS Windows.
2. Nắm rõ các mô tả cơ bản của chương trình với ứng dụng của cryptoproviders (CSP). Xác nhận cách thức tương tác phần mềm client-server.
3. Thiết kế và triển khai phần mềm của một công cụ phần mềm được bảo vệ phù hợp với dữ liệu ban đầu cho thiết kế khóa học.  

# Requirements 
Sử dụng CryptoAPI trong OS Windows và các CSP yêu cầu phát triển một chương trình, đảm bảo bảo mật mã hóa trao đổi files giữa các máy tính khác nhau của 1 mạng máy tính. Chương trình cần thực hiện quá trình mã hóa, hash, và chữ ký số điện tử, để truyền dữ liệu của người dùng sang một máy tính khác. Đối với crytoprovider cần phải sử dụng chuẩn CSP.
Phát triển mạng bảo mật ứng dụng trao đổi giữa 2 máy: client và server.Các thành phần này phải hoạt động đồng thời trên cả các PC khác nhau, ở xa về mặt địa lý và trên một máy tính. Do đó, phần mềm mạng chứa các thành phần mật mã và vận chuyển. Trên thực tế, thành phần mật mã của chương trình mạng cung cấp sự bảo vệ bằng mật mã đối với thông tin người dùng trong hệ điều hành; vận tải - kết nối internet: tổ chức phiên tương tác giữa máy khách-máy chủ và chuyển thông tin người dùng từ người dùng từ mạng này (PC) sang người dùng từ mạng khác (PC thứ hai). Đồng thời, để thiết lập phiên với một PC tùy ý, bạn nên sử dụng địa chỉ ip mạng qua IPv4.  
Một sự khác biệt đáng kể trong sự phát triển của phần mềm mạng
phương tiện từ cục bộ bao gồm việc tạo và trao đổi mạng giữa các PC tương tác với các khóa người dùng đối xứng phiên và mở không đối xứng để chuyển đổi thông tin bằng mật mã. Khi phát triển một ứng dụng mạng, có ba lựa chọn để tổ chức tương tác mạng.
