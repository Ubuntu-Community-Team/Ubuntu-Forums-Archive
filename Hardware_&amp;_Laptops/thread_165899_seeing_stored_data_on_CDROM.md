---
title: "seeing stored data on CDROM"
date: 2006-04-25
forum: Hardware &amp; Laptops
---

### Post by venus06 on 2006-04-25
Have ubunto breezy installed on Acer laptop:) with win 2000k dual boot.
Can access windows ntfs partition fine but cannot acces CDROM correctly:-k 

The CDROM mounts ok but I can only see 3 files :autorun.inf,udfrchk.exe and udfrinst.zl ?

The CDROM ( CD-RW) is written  iso 9660 ??

Any suggestions ??

Thanks

---

### Post by Mr Fat Bat on 2006-05-17
Hi there,

Can you post your /etc/fstab ?

---

### Post by snipe122 on 2006-05-18
your cd seems not be written in iso. looks like UDF-disc-format thats used by directcd for example... this happens as well if you put this cd in an win98 pc. try the following I found through google or burn it as real iso:

[http://lists.freebsd.org/pipermail/freebsd-questions/2004-April/044719.html](http://lists.freebsd.org/pipermail/freebsd-questions/2004-April/044719.html)


greetz
snipe

---

