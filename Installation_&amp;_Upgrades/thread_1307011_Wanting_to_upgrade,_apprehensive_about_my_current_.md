---
title: "Wanting to upgrade, apprehensive about my current dual-boot setup"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Jaunty_Joe on 2009-10-30
Hello everyone. I would like to upgrade to Karmic Koala, however, I have a question. I am currently dual-booting Fedora 11 and Ubuntu 9.04. If you are familiar with Fedora, which I am not, Fedora's boot loader basically takes the reins when it is installed. From the little I've read, Fedora' bootloader will create options for already installed Windows, but will ignore other distro's of Linux. Imagine my surprise when I installed Fedora and had no more Ubuntu (easy fix once I found the post). Anywho...will I have issues if I upgrade to 9.10? My Ubunutu is currently installed on hd1,0. Any help would be much appreciated. 
 
P.S. I know what you are thinking; 'Fedora, really?' But I thought, what the hey, I'll give it a shot. Have spent approximately 2 hours in Fedora to date :D
RPM Fusion ftl

---

### Post by Sensiva on 2009-10-31
You may edit menu.lst of Fedora installation to chainload grub2 of Ubuntu in (hd1,0) by adding these two lines in /boot/grub/menu.lst (in Fedora)

```

title Ubuntu Grub 2
root (hd1,0)
kernel /boot/grub/core.img

```This is how I was doing when testing Karmic pre-releases and it works :D

*EDIT*
Sorry I missed that you are upgrading from Jaunty, read this [http://ubuntuforums.org/showthread.php?t=1305158](http://ubuntuforums.org/showthread.php?t=1305158) then do the upgrade, then add these two lines in /boot/grub/menu.lst (in Fedora)

```

title Ubuntu Grub 2
root (hd1,0)
configfile /boot/grub/menu.lst

```

this will make Grub to load menu.lst of Ubuntu installation

---

### Post by Jaunty_Joe on 2009-10-31
Right on.  I just wanted to make sure that upgrading wouldn't fudge up Fedora's i-go-first -  bootloader.  And worst case scenario, it sounds like I'll just have to re-edit menu.ls like I did originally after I installed Fedora.  Thanks!

---

