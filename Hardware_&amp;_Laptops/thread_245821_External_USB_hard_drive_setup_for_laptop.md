---
title: "External USB hard drive setup for laptop"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by maurizio on 2006-08-28
Dear All:

I am new to Ubuntu and am very impressed so far by its stability and elegance .

I have a dual boot on a Thinkpad T43 and am now trying to setup an external USB hard drive.  I formatted it as ext3 and added this line to etc/fstab:

/dev/hdb1  /media/Firelite ext3   auto, user, owner, rw, exec  0    0

Everything works perfectly after startup, but the problem comes when I close the lid and put the laptop into suspend: the system re-assigns to this USB drive another letter (hdc1), so my backup scripts with rsync don't work any more.

I was wondering whether it might be possible to set it up such that its name and mount point do not change after I put the laptop into suspend or hybernate.

Thank you so much in advance for your help!

Kindest Regards,
Maurizio

---

