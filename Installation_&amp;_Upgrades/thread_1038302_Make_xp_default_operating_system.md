---
title: "Make xp default operating system"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by haran_hockey on 2009-01-12
I am dual booting xp and ubuntu and want to do 2 things:

1. Increase time to choose operating system.

2. Make xp the default operating system so if I don't choose anything, it would automatically choose xp.

---

### Post by oilchangeguy on 2009-01-12
this may help:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by drjonze on 2009-01-12
If you aren't comfortable editing your menu.lst file, just install startup manager. It will do exactly what you're looking for. It's in Add/Remove Programs or type sudo apt-get install startup manager in a terminal

---

### Post by haran_hockey on 2009-01-12
I'm ok editing it but I'm not sure what number to change it to:

> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e88f15f6-a303-441e-a1b5-8d397a6b362e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e88f15f6-a303-441e-a1b5-8d397a6b362e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e88f15f6-a303-441e-a1b5-8d397a6b362e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e88f15f6-a303-441e-a1b5-8d397a6b362e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e88f15f6-a303-441e-a1b5-8d397a6b362e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e88f15f6-a303-441e-a1b5-8d397a6b362e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e88f15f6-a303-441e-a1b5-8d397a6b362e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e88f15f6-a303-441e-a1b5-8d397a6b362e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e88f15f6-a303-441e-a1b5-8d397a6b362e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by briandu on 2009-01-12
If I count right (starting from 1 item is = 0) then XP is 5.

Set it and check

---

### Post by haran_hockey on 2009-01-12
I counted 6- u may of forgot the 'other operating systems' title

---

