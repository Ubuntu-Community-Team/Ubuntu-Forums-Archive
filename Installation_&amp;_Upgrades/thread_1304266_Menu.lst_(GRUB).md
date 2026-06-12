---
title: "Menu.lst (GRUB)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by NightCrawler03X on 2009-10-29
Hi, just a quick question..
I updated a few things, including Linux recently. So a new kernel version became available. I was asked if I wanted to replace /boot/grub/menu.lst with a new version, since the Xubuntu update manager had detected that I had modified it.

So, 2.6.28-16 was the new version, I reject the auto-changes proposed by the update manager, and change menu.lst myself. Of course, I can't load kernel 2.6.28-16; I'm currently using the previous version I have (I always keep old versions around, deleting them is a madman's task, what with volatile changes that occur in Linux). So I obviously made a mistake editing menu.lst

So, my question is:
Can someone with all the latest updates (including Linux 2.6.28-16) show me their /boot/grub/menu.lst file? This is assuming you have Linux kernel 2.6.28-16, and GRUB is configured to be able to load it correctly for you. I want to compare yours with mine so I can see where I went wrong.

Also, it's probably relevant that I'm on Xubuntu 9.04 AMD64 Desktop.

---

### Post by Shazaam on 2009-10-29
```
gksudo gedit /boot/grub/menu.lst
```
Here is mine (minus the UUID)...
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/sda6 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/sda6 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

```
But I cheat. When I edit menu.lst I copy/paste the old/previous entry  and just change the last kernel number on every line. So .15 is now .16. Your hd numbering info will be different so don't use mine.
grub2 in Karmic is different and there are new ways to edit/change grub. There are posts on the forums here that deal with configuring grub2.

---

### Post by NightCrawler03X on 2009-10-29
Yes, I cheat aswell. I copy the last entry, and just change the numbers. Well, turned out it was a rather simple mistake; one of the numbers I forgot to replace.

It was loading /boot/initrd.img-2.6.28-16-generic (from 2.6.28-16, the one I want), but the actual kernel being loaded was /boot/vmlinuz-2.6.28-15-generic (2.6.28-15, the old version).

Well, I'm an idiot. Should definitely pay attention to these things from now on.

So, here is my menu.lst, sans UUID of course:
```
title		Windows XP MCE
root		(hd0,1)
makeactive
chainloader	+1

#Added by myself
title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=UUID-WAS-HERE ro quiet splash vga=775
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

#Added by myself
title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=UUID-WAS-HERE ro  single
initrd		/boot/initrd.img-2.6.28-16-generic


title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=UUID-WAS-HERE ro quiet splash vga=775
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=UUID-WAS-HERE ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=UUID-WAS-HERE ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=UUID-WAS-HERE ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=UUID-WAS-HERE ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=UUID-WAS-HERE ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=UUID-WAS-HERE ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		UUID-WAS-HERE
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=UUID-WAS-HERE ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		UUID-WAS-HERE
kernel		/boot/memtest86+.bin
quiet
```
Gonna reboot now to test these changes.

---

### Post by presence1960 on 2009-10-29
would be pain-free if you allow the update manager to edit your menu.lst. Haven't ever had that mess up on me.

---

