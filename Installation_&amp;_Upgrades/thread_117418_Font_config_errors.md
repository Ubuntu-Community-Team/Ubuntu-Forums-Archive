---
title: "Font config errors?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by clearscreen on 2006-01-14
I just tried to install Ubuntu.. Everything went fine(at least it supports my nForce 4 stuff), the base system was installed, packages were copied, GRUB loader on mbr was placed, and then my system rebooted. Everything went just smoothly. After the reboot, I came to the 2nd part of the install, which would install the copied files from the CD. This went fine until about 70% and I got a spontaneous reboot... When I booted up again, it looked like Ubuntu was properly installed so I entered my login info (note that it didnt spawn X), and then I entered sudo -su and entered my password. When I tried to use apt-get, It told me that there was something wrong with dpkg and that I should run dpkg --configure -a.. This is what I did and it went configuring all kinds of stuff, but there were a LOT of errors on font packages/files. After a while I got another spontaneous reboot (while dpkg was still busy). I tried running X (startx) and it opened some kind of graphical screen with a little white console in my left top side of the screen...

How can I solve the problem that my install just reboots without finishing? I'm very sure the CD I burned is correct.
Ubuntu 5.10 i386
Motherboard: Asus A8N-SLi (nForce 4 chipset)
Video: Geforce 6600GT

Thanks a lot.

---

