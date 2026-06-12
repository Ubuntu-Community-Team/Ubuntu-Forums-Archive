---
title: "external hard drive grub error 17"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by elephantnuts on 2009-10-07
hi guys, im a complete noob when it comes to ubuntu... so firstly i would like to apologise for that...
 
i installed ubuntu onto an external hard drive, when the installation complete i was told to restart the computer so i did and in the boot menu i set it so it boots from the external, and all i get is the grub error 17 and cant do anything from there..
 
i install ubuntu toward the end of the hard drive so i dont know if that makes a difference, i wouldnt expect it to.. i did this because there is some data on the drive i want to preserve.
 
according to this thread: [http://ubuntuforums.org/showthread.php?t=409123](http://ubuntuforums.org/showthread.php?t=409123)
 
> 
Hi,
thank you all for your tips and hints.
 
I finally made it to work. 
 
In my case the problem seem to have been caused by two factors:
- the fact that my Linux partition was located too far away from the beginning of the disc
- the fact that when I boot from my external hard drive it becomes hd0 although it was hd1 during install.
 
The first factor I managed to overcame with GPartEd: I deleted the existing Linux partition and moved the existing FAT 32 partition to the end of the disc leaving the space unused so that the installer could use it.
 
The second factor I overcame with booting via Super Grub Disk and then changing what I had in menu.lst from (hd1,1) to (hd0,1). This did the trick.
 
Thanks again for help!
 
Huckey

 
im not sure if i even need grub because i dont want to select between one OS or Another, as i have them both on different hard drives.
 
if someone could explain exactly what super grub disk is? i take it its a boot cd so i can bypass the error?
and then after that how would i edit the menu.lst?
 
thanks in advance!
 
:)

---

