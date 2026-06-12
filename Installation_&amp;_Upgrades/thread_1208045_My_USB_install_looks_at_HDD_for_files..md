---
title: "My USB install looks at HDD for files."
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by darylt on 2009-07-08
I installed Ubuntu 9.04 fine on a USB stick, but when it boots it starts of just fine then aborts. It looks like it is searching the HDD for the install which obviously is not there.  Think it might be the GRUB files, but not sure what I'm looking at as I'm new to Linux.

---

### Post by earthpigg on 2009-07-08
what method did you use to install ubuntu onto a USB stick? (this is the best method for this, in my humble opinion: system -> administration -> USB startup disk creator)

how much ram does the computer you are trying to boot with have, and does the main hard drive have a swap partition?

---

### Post by pietro_spina on 2009-07-09
I believe I am having this issue as well I'm not even getting Ubuntu loaded. If I remove quiet and splash from the boot args and watch the messages I get the following messages repeating.

```
EXT3-sf: mounted file system with orderd data mode.
kjournald starting. Commit interval 5 seconds.
```

It does this repeating message for about a minute and then drops into a BusyBox built in shell (ash) and offers up a prompt of (initramfs)  

any thoughts? I am bout to pull the hard drives and see if I can just boot the usb stick...

oh and the usb was made using the tool in the admin menu of a jaunty install.

cheers,
-p

---

### Post by darylt on 2009-07-09
I used the Install icon on the desktop as I want to use it as if my 4Gb USB was a HDD. It worked fine under Mandriva but really prefer Ubuntu as I'm new to Linux.
 
 
 
 
 
***[COLOR=red]Computer:[/COLOR]***
 
Toshiba Laptop
 
AMD Turion X2 64bit
ATI Radeon Mobility HD 3650 512 MB
4 GB RAM
250 GB HDD (2Vista Partitions Only)
 
earthpigg -- I just tried the "system -> administration -> USB startup disk" and the same problem. Boots fine and can select from the boot menu fine, but when it tries to load the HDD flashes like mad and then times out.

---

### Post by pietro_spina on 2009-07-09
this [http://ubuntuforums.org/showthread.php?t=1124259](http://ubuntuforums.org/showthread.php?t=1124259) thread pointed me at this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946) bug report where the **absolutely ridiculous** solution is to yank out the USB stick as it starts to read from the hard drives and then put it right back in...

This method worked for me when I had disconnected my HD's and with them connected... This may not be the way you want to repeatedly load up ubuntu, but for me it at least gets me to a point where I have a working session that I can use to fix my grub problems on the HD...

best of luck... 
-p

---

### Post by darylt on 2009-07-10
IT WORKED!!! Thank you. \\:D/
 
 
It looks like its down to the Hardware but now I have a fully working install on my USB...
 
The first thing I did was an Update and now it works straight away every time and I don't have to unplug the USB stick for it to work. (Looks like they fixed the bug)
 
 
 
 
Many thanks again.
 
[CENTER]:smile::smile::smile:[/CENTER]

---

