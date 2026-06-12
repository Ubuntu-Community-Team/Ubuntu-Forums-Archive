---
title: "How do I check load cycle count?"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Zanwar000 on 2007-12-20
I have an Inspiron 1501 Dell Laptop with Ubuntu Feisty and recently I have become worried due to the rumors of the load count increasing in large amounts. I read all the FAQs and information I could find, but I still don't know **how** to check my load cycles. Tools mentioned on blogs/FAQs include smartmontools and smartctl - but I don't know how to use them.

I know Ubuntu says that the load count is not a fault with Ubuntu but with the BIOS itself, but should I use Windows to keep my load cycle count low?

Thnak you for any help.

edit: My device is a TOSHIBA MK8034GS Version: AH30, if that makes a difference.

---

### Post by Milambar on 2007-12-21
The command you are looking for is most probably:

```
sudo smartctl -a /dev/sda | grep 193
```

Although the path /dev/sda may need to be altered, depending on your system.

---

### Post by jespdj on 2007-12-21
Read this thread, it contains everything you need to know:
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by kendon on 2008-01-08
i have exactly the same drive, TOSHIBA MK8034GS Version: AH30. smartctl tells me that my drive "does not support SMART".

any other way to find out the load cycles?

---

