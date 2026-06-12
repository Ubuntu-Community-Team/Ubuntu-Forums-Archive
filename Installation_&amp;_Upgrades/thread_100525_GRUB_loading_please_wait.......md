---
title: "GRUB loading please wait......"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by loker on 2005-12-07
I am a linux noob so forgive me.....I attempted to install the AMD64 version of Ubuntu the install goes without problems the system then restarts and starts loading GRUb it gets to GRUB loading please wait......  and it will just hang there. I have tried switching drives around loading with only the one drive plugged in...I was told disabling LBA in my BIOS could fix it but that just got me error 17 which I knew was something about grub not recognizing the partition so I re-enabled LBA and I am back to Grub loading please wait.....any help would be much appreciated!

---

### Post by loker on 2005-12-07
I just got home and here is a copy of my menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-amd64-generic Default 
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Default (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

