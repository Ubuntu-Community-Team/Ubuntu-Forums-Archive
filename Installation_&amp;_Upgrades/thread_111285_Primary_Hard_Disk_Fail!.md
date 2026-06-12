---
title: "Primary Hard Disk Fail!"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by greymoose58 on 2006-01-02
I've got a PII 233MMX that comes up with primary hard disk fail at every boot. I carried on and the Ubuntu installation went fine (hdd partitioned, base system installed, etc) until I had to boot from the HDD. Same error again.

I've swapped out the disk, the cable, changed the way the disk is detected, changed every setting in the BIOS I can find that looks even remotely like it is related to the IDE ports. I've reloaded the default Bios settings and removed the battery from the motherboard. I attempted to reset the bios using the three pin jumper next to the battery to no avail. When all of this failed I went to Google - no help.

I'm confident the HDD is ok (it seems like only the CMOS that doesn't agree) so  does anyone know if there may be a setting I have missed or another reason for the error message?

Thanks in advance.

---

### Post by Sef on 2006-01-02
Have you tried reinstalling with a different install disk?

Maybe the CD you have is bad.

---

### Post by greymoose58 on 2006-01-02
I considered that but I haven't tried it for two reasons:

1. I installed to my office machine from the same CD recently

2. The error occurs before the machine even boots from the CD

Thanks for the thought.

---

### Post by greymoose58 on 2006-01-08
It turns out that the power cable going to the hard drive was faulty. It wasn't getting enough power to spin up for the CMOS to detect it. Funnily enough it was getting enough power to allow me to install Ubuntu to the hard drive. Go Figure.

Anyway, thanks.

---

