---
title: "System freezes frequently!"
date: 2009-11-27
forum: Hardware
---

### Post by mahdif62 on 2009-11-27
I have a strange problem. With new i.e ubuntu karmic, openSuse 11.2, Fedora 12, mandriva 2010 my system freezes at a random point. On all distros I install the latest nvidia driver for my 8500GT card, following distro-specific procedures. Sometimes when I move my mouse, or try to drag windows, a freeze happens and I can't even kill X or switch to a virtual console and I have to reset!
My system is an Intel core 2 Duo box with Asus P5B mobo and Nvidia 8500GT video card. All my linux partitions are ext4 formatted. Can you please help me solve this problem?

---

### Post by Sloma on 2009-11-27
Hi, You're not alone, I have exactly the same issue on my system, only that I have GeForce Go 6200.

---

### Post by janascii on 2009-12-07
I've suddenly had issues with this as well.  I thought it was after the kernel update I did today, but now its happening in all my older ones too.  

I read the change log and found this:
> Fixed a randomly occurring X server crash caused by the PixmapCache option.

Anyone had luck with the 190 series drivers?  I'll be trying them and posting with results.  Hopefully I don't fall in the configuration hell that can be nvidia drivers.

---

### Post by janascii on 2009-12-07
So back already...

Nvidia was nice for once and upgraded without a hitch version 190.42

However, its still freezing up.  I've been reading about firefox causing this elsewhere so I'm trying that next.

Also I've tried all the kernel versions that are in my grub menu and all are doing the same thing so I don't think its related to the kernel update I did today, probably something else that was also in the list that I'm forgetting about.

---

### Post by janascii on 2009-12-07
More here
[http://ubuntuforums.org/showthread.php?t=1309015](http://ubuntuforums.org/showthread.php?t=1309015)

---

