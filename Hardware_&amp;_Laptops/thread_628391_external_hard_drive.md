---
title: "external hard drive"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by findlj on 2007-12-01
Hello,  I've recently set up a dual boot Ubuntu/XP computer.   I runs great and I love the Linux.  However, I'd like to back up the Linux side now but my 100GB Maxtor OneTouch III external drive will not mount.   It connects via USB and I can get Ubuntu to see the drive (but not mount) if I plug both USB connectors into my machine.  Ubuntu tells me it cannot mount the drive.Note that with one connector only the system will not even see the drive.  

I'm not opposed to purchasing another ext drive if need be.   Any suggestions?

---

### Post by prodezigner on 2007-12-01
well... first...

sudo apt-get install ntfs-3f autofs

then after that, plug in your drive and type in:

dmesg | tail

(all this is in terminal btw)...

post your results.

---

