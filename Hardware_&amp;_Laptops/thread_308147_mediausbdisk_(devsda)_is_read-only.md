---
title: "/media/usbdisk (/dev/sda) is read-only"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by chess64 on 2006-11-27
A few months ago I had ubuntu (dapper drake) installed. I didn't have any problems then, but a few months after that I installed SuSE 10.0 and now (a few months after I installed SuSE) I just installed ubuntu 6.06 again yesterday. However, this time, I cannot copy files onto my usb devices. It says "cp: cannot create regular file `/media/usbdisk/<filename>': Read-only file system". Also, "tail /var/log/syslog" gives a whole bunch of errors like 'FAT: Filesystem panic (dev sda)' and 'invalid access to FAT (entry 0x0fc4e461)' where the entry is different each time. And "dd if=<filename> of=/dev/sda" seems like it works, but it really doesn't... :(

This is very annoying...

Oh yes, I almost forgot... I'm a ubuntu newbie :)

---

### Post by chess64 on 2006-12-04
Well, thanks for all the help guys! However, I will now be using Gentoo.

---

