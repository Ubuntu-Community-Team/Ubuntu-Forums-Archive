---
title: "dell inspiron 6000 and fan control"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by ``bobby`` on 2006-01-15
Hello,

The fans run constantly on my dell inspiron 6000 and I cannot get them to turn off.  I have tried the i8kutils pacakge but get the following:

$ dmesg | grep i8k
[4294685.825000] i8k: not running on a Dell system
[4294685.825000] i8k: vendor=Dell Inc., model=Inspiron 6000, version=A09
[4294685.825000] i8k: unable to get SMM Dell signature
[4294685.825000] i8k: unable to get SMM BIOS version

I have searched the forums but cannot find anything that seems to work.  Any help would be greatly appreciated.

Thanks!

---

### Post by cykze on 2006-05-01
Is the i8k module loaded?

lsmod | grep i8k

---

