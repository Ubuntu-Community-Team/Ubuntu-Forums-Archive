---
title: "GRUB Bootloader Advice Needed"
date: 2008-11-10
forum: General Help
---

### Post by Vince4Amy on 2008-11-10
Okay So after I resolved a problem with my Vista boot loader (more infomation):

[http://ubuntuforums.org/showthread.php?t=976816](http://ubuntuforums.org/showthread.php?t=976816)

I now have this problem with GRUB, which is whenever I reinstall it I get the error code 22, which I assume is the files not being found. 

So I wiped the HDD which Kubuntu was on and reinstalled it and told it to store the GRUB Bootloader on the MBR as usual, but I still get Error 22 which is strange.

My Vista and MBR are on /dev/sda1
My Kubuntu is on /dev/sdc2

It worked fine this way before I wiped Kubuntu and installed Vista on sdc, and when I removed the extra Vista fixed the bootloader and then reinstalled Kubuntu I get the Error 22.

---

### Post by cariboo on 2008-11-10
You should slow down and stop installing OS's to try and fix your problem. If you had   searched here in the forums, you would have seen many references to Super Grub Disk If you download and burn the cd, then boot from it, it will take less than 5 minutes to fix your problem. you can get Super Grub Disk here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Jim

---

