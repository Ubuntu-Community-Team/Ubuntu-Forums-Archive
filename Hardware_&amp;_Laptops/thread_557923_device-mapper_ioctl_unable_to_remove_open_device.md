---
title: "device-mapper: ioctl: unable to remove open device"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by gubemton on 2007-09-23
I have a problem, that is probably not new but I can't exactly tell you when it startet. I noticed it by chance in my /var/log/messages and I think thats the reason why my Ubuntu is so slow.

I get this message 7 times per second in my /var/log/messages:

```
Sep 14 21:35:05 thibaud kernel: [ 2348.300911] device-mapper: ioctl: unable to remove open device sda6
```

I couldn't find out what sda6 is but I guess it is a USB-Stick or an external hard-drive I did not correctly unmount. But how can I unmount it? Or where can the command to unmount in can come from, so that I can delete it, because now my Ubuntu is so slow.

I'm happy about any form of advice. Thanks!

---

### Post by EnterDaMatrix on 2007-09-26
Bug is filed: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/119315/](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/119315/)

I had this same problem and it can be fixed by removing all the packages starting with evms.

---

### Post by gubemton on 2007-09-30
My problems are not the same as in the bugreport, are they?
I wonder if I can get problems if I just delete the evms-packages.

---

### Post by gubemton on 2007-10-03
Can there occure problems if I just delete the evms-packages?

---

### Post by gubemton on 2007-10-08
I'll ask another way: What are the evms-packages for and do I really need them?

---

### Post by gubemton on 2007-11-19
The problem finally fixed itself while updating to Gutsy but I wanted to tell you that it is really frustrating when you don't get an answer. I know, you don't get payed for it, but I was frustrated nevertheless.

---

