---
title: "Reset GRUB and files access permission in Ubuntu 8.04"
date: 2008-11-27
forum: General Help
---

### Post by hansprawira on 2008-11-27
May day, may day. my PC has 2 hard disk, one as master(Blankon 3.0) and other as slave (Ubuntu 8.04). Each time I start my computer, GRUB always show me which OS I want to access, Ubuntu or Blankon. Because mostly my files is using Chinese characters, Ubuntu is the only choice. Unfortunately because of some accident, Blankon 3.0 is formatted and replace by PCLinux 2007. The point is: I have so many files in Ubuntu 8.04 that I use daily and I cannot access them from PCLinux. I cannot either login to Ubuntu 8.04 because GRUB in Blankon which arrange the loading is now disappeared. I need to know 2 things: 1. How to reset GRUB in Ubuntu so I can login again. 2. How to access the files in Ubuntu from PCLinux, since now we don't have the permission to access files. I have heard some rwx stuff but very complicated for me. Please help.

---

### Post by Peter09 on 2008-11-27
Here is another thread which shows how to recover your Grub.

[http://ubuntuforums.org/showthread.php?t=521388](http://ubuntuforums.org/showthread.php?t=521388)
*edit - and another

[http://basrahmat.wordpress.com/2008/11/05/recovery-ubuntu-grub/](http://basrahmat.wordpress.com/2008/11/05/recovery-ubuntu-grub/)

---

### Post by caljohnsmith on 2008-11-27
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And please identify your partitions. Next post the output of:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```
And we can work from there if you want.

---

