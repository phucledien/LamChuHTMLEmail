# Xây dựng một template HTML Email từ đầu

![template final](https://cms-assets.tutsplus.com/uploads/users/30/posts/9386/final_image/email-buil-final.png)

Cách tốt nhất để hiểu được một vấn đề nào đó một cách rõ nhất, chính là tự mình làm nó từ đầu. Hôm nay, ta sẽ thực hiện điều tương tự vậy, chúng ta sẽ tự xây dựng một template HTML Email từ đầu.

Nếu bạn đang tìm kiếm một cái gì đó có sẵn, có rất nhiều trang cung cấp điều đó cho bạn. Tuy nhiên, chắc chắn là nó không miễn phí. Bạn có thể tham khảo ở [đây](https://elements.envato.com/web-templates/email-templates?_ga=2.32880698.56300719.1507171594-551793807.1507171555)

Hoặc bạn cũng có thể thuê một designer để làm điều đó cho bạn. Nhưng tại sao bạn lại không tự làm điều đó thay vì bỏ ra 50$ =]. 

## Chuẩn bị
Đầu tiên, mình đã chuẩn bị sẵn các thứ cần thiết trong thư mục part-2-resources, bạn có thể lấy về ở đó.

Ok, tiếp theo bạn sẽ tạo một file html và bắt đầu với XHTML doctype như đã đề cập ở bài [trước]()

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
 <head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <title>Demystifying Email Design</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
</head>
</html>
```

Đầy đủ hết rồi, giờ bắt đầu làm thôi :))

## Tạo phần Body và Main Table

Đầu tiên, ta sẽ tạo phần cấu trúc của email, bắt đầu với tag `<body>`. Chúng ta sẽ set margin và padding cho body tag về 0 để xoá hết tất cả khoảng trắng.
Chúng ta cũng sẽ tạo một table với độ rộng bằng 100%. Thật ra, table này đóng vai trò như body tag trong email của chúng ta. Tuy nhiên do việc styling cho body tag không được hổ trợ, do đó chúng ta phải style trên table này =]. Ví dụ như bạn muốn thêm background color vào phần body của email, thay vì chỉnh trên body tag, bạn phải thêm background-color trên table.

Tiếp theo, ta sẽ set cellpadding và cellspacing của các ô table (cell) về 0 hết, để xoá hết các khoảng trắng.

**Chú ý:** Chúng ta sẽ để thuộc tính `border="1"` cho tất cả các table, nhờ vậy, ta có thể quan sát được cấu trúc của layout và dễ dàng tuỳ chỉnh hơn. Sau khi làm xong hết thì ta sẽ xoá hết các thuộc tính này bằng Find & Replace.
Đây là code HTML cho main table của chúng ta.

```
<body style="margin: 0; padding: 0;">
 <table border="1" cellpadding="0" cellspacing="0" width="100%">
  <tr>
   <td>
    Hello!
   </td>
  </tr>
 </table>
</body>
```

![example](https://cdn.tutsplus.com/webdesign/uploads/2013/06/1.jpg)

> Nếu các thuộc tính có sẵn trên HTML thì chúng ta nên sử dụng chúng thay vì sử dụng CSS

OK, bây giờ chúng ta sẽ đặt vào cái table mới tạo vừa nãy một cái table khác. Table này sẽ được canh giữa, và có độ rộng là 600 pixels. 600 pixels là độ rộng an toàn tối đa cho email của bạn để có thể hiển thị tốt nhất trên hầu hết độ phân giải ở các desktop cũng như webmail clients.

Ta sẽ set thuộc tính width bằng HTML thay vì CSS. Nguyên tắc vàng trong việc viết một HTML email là: "Nếu các thuộc tính có sẵn trên HTML thì chúng ta nên sử dụng chúng thay vì sử dụng CSS".

Chúng ta sẽ thay cái chữ "Hello!" nhỏ nhỏ ở cái main table với đoạn code sau:
```
<table align="center" border="1" cellpadding="0" cellspacing="0" width="600" style="border-collapse: collapse;">
 <tr>
  <td>
   Hello!
  </td>
 </tr>
</table>
```
Chúng ta cũng thêm vào các thuộc tính inline style như "border-collapse: collapse;". Nếu chúng ta không làm vậy, các phiên bản mới hơn của Outlook sẽ thêm vào một khoảng trống nhỏ giữa bảng và border của chúng ta.

![examlple](https://cdn.tutsplus.com/webdesign/uploads/2013/06/2.jpg)

## Tạo sườn và Header

Trong bản thiết kế, ta thấy email được chia làm ba phần, do đó, ta sẽ tạo mỗi phần là một hàng (row).

Chúng ta sẽ copy paste cái row của cái bảng vừa nãy mới làm thành ba phần. Mình đã thêm vào các chữ ở mỗi row để các bạn dễ phân biệt

```
<table align="center" border="1" cellpadding="0" cellspacing="0" width="600">
 <tr>
  <td>
   Row 1
  </td>
 </tr>
 <tr>
  <td>
   Row 2
  </td>
 </tr>
 <tr>
  <td>
   Row 3
  </td>
 </tr>
</table>
```
![example](https://cdn.tutsplus.com/webdesign/uploads/2013/06/3.jpg)

Bây giờ, ta sẽ thêm màu sắc theo mẫu thiết kế. Ta sẽ sử dụng thuộc tính `bgcolor` có sẵn của HTML để thêm màu thay vì sử dụng CSS. Luôn nhớ phải sử dụng đầy đủ 6 kí tự của mã màu hex, nó có thể không hoạt động nếu chúng ta rút gọn thành 3 kí tự.

```
<table align="center" border="1" cellpadding="0" cellspacing="0" width="600">
 <tr>
  <td bgcolor="#70bbd9">
   Row 1
  </td>
 </tr>
 <tr>
  <td bgcolor="#ffffff">
   Row 2
  </td>
 </tr>
 <tr>
  <td bgcolor="#ee4c50">
   Row 3
  </td>
 </tr>
</table>
```

![example](https://cdn.tutsplus.com/webdesign/uploads/2013/06/4.jpg)

OK, tiếp theo ta sẽ tập trung vào row 1. Chúng ta sẽ tuỳ chỉnh padding của cell đó và thêm hình vào.

### Sử dụng Padding

Khi sử dụng padding trong email, bạn phải luôn khai báo đầy đủ tất cả các giá trị (top, right, bottom, left) nếu không có thể sẽ bị lỗi. Chúng ta có thể sử dụng cách shorthand, ví dụ: `padding: 10px 10px 8px 5px;`, tuy nhiên, nếu gặp vấn đề gì đó bạn nên viết lại dưới dạng longform, ví dụ: `padding-top: 10px; padding-right: 10px; padding-bottom: 8px; padding-left: 5px;`.

 

