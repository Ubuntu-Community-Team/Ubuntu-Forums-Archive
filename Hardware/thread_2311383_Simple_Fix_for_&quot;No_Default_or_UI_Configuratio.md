---
title: "Simple Fix for &quot;No Default or UI Configuration Directive Found!&quot;"
date: 2016-01-26
forum: Hardware
---

### Post by markackerman8@gmail.com on 2016-01-26
Simple?
go into BIOS / Boot Options, and put the HDD as the top selection ... (move USB-HDD? to below it)

Now for a further explanation:
When I googled this, it is a popular error, which almost always is associated with a problem booting form a USB Drive.  It's normal solution involves making the USB drive "Bootable". i.e.) no just a data drive.  My issue was periodically getting this error during a restart.  And low and behold my Boot menu was looking for a USB drive first (In Boot Options), which in itself is not usually a problem as it should just bi-pass this when a "Bootable USB stick" is not plugged in.  However I have many usb devices and I think the grub loader or Bios (in this case) was just getting SIMPLY confused.

I hope this helps others - a real simple fix for an annoying issue.  (I even reinstalled arghhh, just to find it again)

Cheers, Mark:p

p.s. Ubuntu-Gnome / Teak Tool / Extensions make the best desktop environment I have ever seen on the planet.  Even makse MAC books look dull.:D

---

### Post by markackerman8@gmail.com on 2016-06-10
I am going senile, 

I had this problem again, and found my own thread to fix it, yep it worked again.

---

