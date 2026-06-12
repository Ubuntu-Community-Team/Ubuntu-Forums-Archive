---
title: "Unbuntu root= path for livecd??"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by jtp755 on 2008-12-24
Good evening!

I have a Fujitsu Lifebook (B-2562) that i would like to install Ubuntu on. It does not have a cd-rom so i have made a boot disk to use driers to access a usb-cdrom and got things working there. My problem is that it is a DOS boot disk and uses linld.com to launch the linux part. I can launch the kernel (/casper/vmlinuz) but it gets to where it wants to load the root device and fails/ I have tried /dev/ram, /dev/rd0, /dev/ram0, /dev/sda1, etc. and can not get any to work. Can someone point me in the right direction? Thanks!

linld command i am using:
d:\>a:\linld.com image=vmlinuz initrd=initrd.gz cl=root=/dev/ram

Thanks!!

---

### Post by albinootje on 2008-12-24
> **jtp755 said:**
> 
d:\>a:\linld.com image=vmlinuz initrd=initrd.gz cl=root=/dev/ram

This posting [http://ubuntuforums.org/archive/index.php/t-244918.html](http://ubuntuforums.org/archive/index.php/t-244918.html) adds more options which might be important to add.
See also here :
[http://ubuntuforums.org/archive/index.php/t-524238.html](http://ubuntuforums.org/archive/index.php/t-524238.html)

---

