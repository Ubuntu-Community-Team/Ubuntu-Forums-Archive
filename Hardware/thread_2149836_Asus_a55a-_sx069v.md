---
title: "Asus a55a- sx069v"
date: 2013-05-30
forum: Hardware
---

### Post by KingOfTheNothing on 2013-05-30
Hi!

I have used ubuntu on some laptops for years and I love it! Recently I bought a new laptop ASUS A55A- SX069V configuration below. I tried to install the latest 13.04 but when rebooting as last step of installation it fails to start. As I understand this 13.04 version is developed for amd processors not for intel.** When will an intel version be available?** 

I tried to install 12.03 (32 bit) but the DVD/CD will not start when booting??

I tried the windowsinstaller but it chooses amd 64 version as default not poosible to change!

[B]I am very unhappy anyone with any advice what to do or which version to go for please help!!! Many thanks in advance!!!
[/B]
ASUS A55A- SX069V
CPU: i7- 3610QM
Memory: 4 GB
Graphic: Intel HD 4000

---

### Post by ajgreeny on 2013-05-30
The amd.64 versions are not just for amd CPUs, but work fine with intel as well, so there's no need to worry about that.  

The fact that you can not even boot a 32 bit CD would tend to point to  a problem with UEFI and GPT partitions instead of the old style BIOS, so have a look at  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to see if that gives you any  clues.  From the live CD see what output you get from ```
sudo fdisk -l
``` as that may also help give us a clue.

---

### Post by KingOfTheNothing on 2013-05-30
Hello! I managed to find a version that works great for my laptop here:[http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)  the version x86 works great.

---

