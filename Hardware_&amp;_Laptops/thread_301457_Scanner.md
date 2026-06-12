---
title: "Scanner"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by Pengwyn44 on 2006-11-17
When I first installed Ubuntu Xsane recognised the scanner and operated it but now it does not. I get an error Message "Failed to open device "Snapscan
:libusb:004:002" Invalid argument.
The scanner still works in Windows so the problem is not with it.
Can anyone suggest what the problem is and how to fix it please?

---

### Post by mitch.c on 2006-11-17
> **Pengwyn44 said:**
> When I first installed Ubuntu Xsane recognised the scanner and operated it but now it does not. I get an error Message "Failed to open device "Snapscan
:libusb:004:002" Invalid argument.
The scanner still works in Windows so the problem is not with it.
Can anyone suggest what the problem is and how to fix it please?
When I have trouble with xsane not recognizing or communicating with my scanner, the first thing I do is:
```
$ rm -rf ~/.sane
```
Works everytime. YMMV.

---

### Post by Pengwyn44 on 2006-11-18
Thanks for the tip. When I booted up Ubuntu 6.06 to try out your tip XSane decided to work! There's a gremlin in it somewhere.

---

