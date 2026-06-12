---
title: "Disk error 80..."
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by jspace on 2006-07-20
HI, I am having a problem istalling Xubuntu on an old acer machine that I have:
P133
48MB EDO
1GB hdd
I dont know what model it is, all I know is it was $10 (w/ broken monitor :( ) and had Windows 95 on it. It does boot from CD but using Dapper gives me this:
> ISOLINUX 3.11 Debian-2006-03-16 isolinux: Disk error 80, AS = 4240, drive 81

Boot failed: press a key to retry...
The strange thing is I have another Debian install on the hdd (30-r6 I believe) but nothing other than disk 7 of that set will boot. Um.. I need help ](*,)

---

### Post by Sef on 2006-07-26
On [URL="http://syslinux.zytor.com/archives/2002-August/000738.html"]syslinux,
[/URL] I found this post about disk error 80:

> Disk error 80 usually means your BIOS is broken, but if you give us the 
*entire* output of isolinux-debug.bin we might be able to give you a 
more useful answer.

> The strange thing is I have another Debian install on the hdd (30-r6 I believe) but nothing other than disk 7 of that set will boot.

It can get around the error some how.  Probably avoids the broken area on the BIOS.

---

