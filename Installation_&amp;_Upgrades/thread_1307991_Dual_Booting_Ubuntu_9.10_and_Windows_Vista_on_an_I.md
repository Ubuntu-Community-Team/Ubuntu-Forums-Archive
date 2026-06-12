---
title: "Dual Booting Ubuntu 9.10 and Windows Vista on an Intel ICH10R Raid"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by gallocs on 2009-10-31
Hello everyone. I am fairly new to the linux scene, with very little linux experience. I am trying to setup a dual-boot option on my computer that would allow me to choose between Ubuntu 9.10 and Windows Vista. Now, I do know that Ubuntu 9.10 sees my raid setup, yet, it doesn't detect my Vista installation. So whenever I continue the installation and boot into Ubuntu, I still have access to my other partitions on the Raid, yet I cannot get GRUB, or anything else for that matter, to boot into Vista. I don't mind reformatting, or installing things in a different order. Any advice would be greatly appreciated.

(On a side note, I am using the 64-Bit version of Ubuntu 9.10)

EDIT: Problem solved. I followed part of this guide. [https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.04%20%28Jaunty%20Jackalope%29 ]("https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.04%20%28Jaunty%20Jackalope%29")
After having installed Ubuntu, I ran a terminal window, and used the command: $ sudo gedit /boot/grub/menu.lst and added the following in the boot menu options:

title           Windows
rootnoverify (hd0,2)
makeactive
chainloader +1

---

