---
title: "can't boot from 9.04 cd"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by henrietta on 2009-07-19
Hi, I'm trying to install jaunty on a emachines e520. It's got 8.10 installed, but I gave up on getting any kind of networking operating, so I'm trying to install from cd.

I downloaded 9.04 on my imac running osx, then burned an iso disk. When I put it in the e520, it mounts and the contents can be extracted and viewed, but I can't get it to boot. Can I install 9.04 without booting from the CD? Any suggestions for getting it to boot?

thanks
-JH

---

### Post by merlinus on 2009-07-19
Did you burn it as a disk image, and not as a data disk, and at no more than 4x?  Also, you may wish to checksum the .iso:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by henrietta on 2009-07-19
"get info" on the mac shows "type" as "iso disk image". 

I ran md5 from terminal and and the hash matches. 

The disk is readable on the emachines e520 running ubuntu 8.10, and can be browsed, but will not boot. I put the internal optical drive at number one in the boot order.

stumped...

-JH

---

### Post by henrietta on 2009-07-19
Okay, I tried copying the disk image to a usb flash drive, which will not boot either. I set it to number 1 in the boot sequence.

Can I get any useful information from GRUB?

-JH

---

### Post by merlinus on 2009-07-19
I don't think grub can tell you anything about a bootable external disk.

Is the version you downloaded compatible with your processor?

---

### Post by henrietta on 2009-07-19
Solved! I burned a disk from the flash drive on the emachines E520, and it liked that a lot better than the disk I burned on the imac.

-JH

---

### Post by merlinus on 2009-07-19
Escellent!  Many times disks burned on one drive will not work on another.  Just another vagary of computers!

---

