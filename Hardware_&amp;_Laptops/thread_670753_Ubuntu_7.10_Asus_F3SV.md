---
title: "Ubuntu 7.10 Asus F3SV"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Samfisher on 2008-01-17
Anyone with an Asus F3SV:

I just bought a new one and I would like to dual-boot Ubuntu 7.10 with Vista Ultimate. Has anyone tried this? Did both Ubuntu and Vista work well?

Also, if ever the need arises to remove Ubuntu (and GRUB) and go back to single-booting Vista, I would like to be able to restore Vista's MBR. However, I only have the Asus Recovery DVD that was bundled with the laptop (and the recovery partition). Can I restore the MBR using the recovery dvd/partition or do I have to obtain a Vista Install CD/DVD?


Thanks for all your help in advance!

---

### Post by i59b on 2008-01-19
I've been dual booting Vista and Ubuntu 7.10 very successfully.  In fact, it's a necessity since my Vista partition has become corrupt 3 times in 5 months.  This has nothing to do with linux, but Vista's inability to cope with a hard reboot.  (I wouldn't have to hard reboot if Vista didn't lock up, but that's another complaint).  Whatever you do, don't expect to be able to resize the Vista partition either.  That didn't end happily for me.  I had to repartition, reinstall Vista, then install linux.  Don't delete the very first partition or your recovery CD won't work.

I haven't tried to restore the Vista MBR.  I would try this utility in Windows BEFORE deleting my linux partition. [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

Make sure you start the Ubuntu live CD in safe graphics mode.  After the installation, the restricted drivers manager does the rest.

I haven't got the F3SV webcam working yet, but I haven't invested too much time in it.    [http://www.linlap.com/wiki/Asus+F3SV](http://www.linlap.com/wiki/Asus+F3SV)

---

