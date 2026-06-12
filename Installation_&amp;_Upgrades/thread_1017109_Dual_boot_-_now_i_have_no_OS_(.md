---
title: "Dual boot - now i have no OS :("
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by pmq on 2008-12-20
I had setup a dual boot everything was fine but i felt i wanted to install ubuntu to another hdd i have, so i used storage disk manager in vista and deleted and formatted the ubuntu partition, which was on the same disk as vista,
however i shut down my machine and came back to it earlier but it doesnt boot.

All i get in the screen is...

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22.

What does this mean? How can i get around this?

Thanks

---

### Post by Amof on 2008-12-20
Well you changed the drivers around so GRUB is trying to boot an operating system that isn't there. I see 2 ways to fix this issue:

1. Reinstall Grub [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
2. Use a live CD to edit the /boot/grub/menu.lst file.

---

### Post by albinootje on 2008-12-20
> **pmq said:**
> I had setup a dual boot everything was fine but i felt i wanted to install ubuntu to another hdd i have, so i used storage disk manager in vista and deleted and formatted the ubuntu partition, which was on the same disk as vista,
however i shut down my machine and came back to it earlier but it doesnt boot.

Grub needed the Ubuntu partition to boot everything.

You need to fix your bootloader first.
Apparently this helps i read elsewhere :
[http://en.wikipedia.org/wiki/EasyBCD](http://en.wikipedia.org/wiki/EasyBCD)

---

### Post by caljohnsmith on 2008-12-20
If you install Ubuntu to your other HDD and accept the default of having Grub installed to /dev/sda, then you will get your dual boot back. If you want to boot Vista in the meantime, you can restore a Windows MBR (Master Boot Record) to the Windows HDD by booting your Live CD and doing:
```
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot into Vista. Let me know how it goes.

---

### Post by infamous-online on 2008-12-20
If possible never install the two Oses on the same harddrive. Always use at least two seperate disks.

I've done this once and never looked back, I lost all of my windows stuff due to me install fedora at the time onto my windows hd.

Now that I've been exclusively been using ubuntu with xp for over 4 years, I never have them on the same harddrive ever! I always make sure to install ubuntu on it's on harddrive so if something goes wrong, it doesn't interfere with my windows installation and vice versa.

I know I probably didn't mention anythingf worthwhile towards solving your problem, but atleast I did provide you with something to think about in the future. ;)

---

