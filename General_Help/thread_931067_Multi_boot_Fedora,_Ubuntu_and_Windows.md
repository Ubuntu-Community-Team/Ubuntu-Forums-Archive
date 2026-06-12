---
title: "Multi boot Fedora, Ubuntu and Windows"
date: 2008-09-26
forum: General Help
---

### Post by parakeets11 on 2008-09-26
Okay, I need a Red Hat OS, Debian OS, and a Windows OS, so I'm trying to multiboot Fedora, Ubuntu, and Windows.  my question is how would I do this?  And does Ubuntu's GRUB recognize other Linux Distros, or does it only recognize Windows?

---

### Post by ThrobbingBrain66 on 2008-09-26
All you have to do is install the Operating Systems.  First, use a Gparted LiveCD to set up your partitions.  Then perform the installs.  Since I prefer Ubuntu's GRUB menu, I would install in this order:

1. Windows
2. Fedora (choose not to install the bootloader)
3. Ubuntu (install the bootloader)

If you do it this way, you won't be able to boot Fedora until after Ubuntu is installed and adds the partition to GRUB.  This setup will show Ubuntu as your main OS and the other two will be added to GRUB as "Other Operating Systems".

---

### Post by parakeets11 on 2008-09-26
Thank you.  I've been wondering how to do this lol.

---

### Post by parakeets11 on 2008-09-28
I have all the Operating systems installed now, but I can't open Fedora from the GRUB menu.  I've been looking on the web for how to do it but everything i tried just doesnt work.

My grub looks like this:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5a8225c5-c683-4773-9008-264ed11ce0f6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5a8225c5-c683-4773-9008-264ed11ce0f6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title           Fedora 9
root 		(hd1,1)
savedefault
makeactive
chainloader     +1

```


Is there a way that I can re-detect the Operating systems?

Or, how would I add Fedora to my grub, chainloading doesnt work apparently.

---

