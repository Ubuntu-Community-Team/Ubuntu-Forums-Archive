---
title: "Strange problem with recognition of external hard drive"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by composer84 on 2007-04-14
[FONT="Georgia"][COLOR="DarkRed"]I recently purchased an usb 2.0 external hard drive case for a 500gb serial ata hard drive. The drivers for the external hard drive have been installed and, according to the device manager, is working properly. However, the drive has not appeared in My Computer. I've been fooling around with it for the better part of two weeks to no avail. Can anyone out there help a less-than-tech-savvy composer?[/COLOR][/FONT]

---

### Post by taurus on 2007-04-14
You need to mount it before you can use/access it in Ubuntu.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

