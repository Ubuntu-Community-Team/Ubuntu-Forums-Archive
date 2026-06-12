---
title: "[Ubuntu 10.10 32bit] ASUS X5DC - Install Video Drivers"
date: 2010-10-15
forum: Hardware
---

### Post by Deviling Master on 2010-10-15
Hi, i have an Asus X5DC Series (model should be K50C). I've installed Ubuntu 10.10 i386 version.

The problem: In monitor options i have only 800x600 resolution and i can't work like this....

I've already read:
- [http://forum.ubuntu-it.org/index.php/topic,415013.0.html](http://forum.ubuntu-it.org/index.php/topic,415013.0.html)
- [http://forum.ubuntu-it.org/index.php?topic=349921.0](http://forum.ubuntu-it.org/index.php?topic=349921.0)
- [http://wiki.ubuntu-it.org/Hardware/Video/SisXgiVolari/Sis771-671?highlight=%28sis%29]("http://wiki.ubuntu-it.org/Hardware/Video/SisXgiVolari/Sis771-671?highlight=%28sis%29")
- [http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)
- [http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html](http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html)
- [http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html](http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html)

I've tried ALL solution into the above links without success.....
At the reboot i get a very strange resolution/colors window and after few seconds start the text mode with command line.
To get back work again i have to delete xorg.conf with
```
sudo rm /etc/X11/xorg.conf
```After this delete if i reboot Ubuntu works again....

Under Windows 7 i have 1366x768 resolution, so if is possibile i wanto to set this one in Ubuntu too.

The VGA controller is:
```
VGA Compatibile Controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```Thanks for your help.... i really can't work with 800x600 resolution....

---

