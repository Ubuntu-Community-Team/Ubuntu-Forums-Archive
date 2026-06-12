---
title: "Ubuntu Studio 9.04 will not boot"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by jhouse59 on 2009-05-10
I just installed Ubuntu Studio 9.04 on a second hard drive. I've got Windows 7 on one. When I boot my computer I don't get a choice to choose Windows or Ubuntu Studio. It just boots into Windows.
Here is what my menu.1st file says:

> 
title		Ubuntu 9.04, kernel 2.6.28-3-rt
uuid		0611b74a-488b-4f87-9710-144070aac357
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=0611b74a-488b-4f87-9710-144070aac357 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid		0611b74a-488b-4f87-9710-144070aac357
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=0611b74a-488b-4f87-9710-144070aac357 ro  single
initrd		/boot/initrd.img-2.6.28-3-rt

title		Ubuntu 9.04, memtest86+
uuid		0611b74a-488b-4f87-9710-144070aac357
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows Vista (loader)
rootnoverify	(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1

Thanks.

---

