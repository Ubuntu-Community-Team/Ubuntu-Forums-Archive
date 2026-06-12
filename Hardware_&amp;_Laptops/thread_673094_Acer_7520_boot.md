---
title: "Acer 7520 boot"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by aprilian bandit on 2008-01-20
I couldn't get my laptop to boot when I installed as a single (80GB) partition, so I made a 75GB partition during install - somehow this made some difference, but now I get this screen
```
Ubuntu 7.10, kernel 2.6.22-14-386
Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Ubuntu 7.10, kernel 2.6.22-generic (on /dev/sda1)
Ubuntu 7.10, kernel 2.6.22-generic (recovery mode) (on /dev/sda1)
Ubuntu 7.10, memtest86+ (on /dev/sda1)
```
To boot I have to go in to 
```
Ubuntu 7.10, kernel 2.6.22-14-generic
```
 where I find 
```
root (hd0,2)
kernel  /boot/vmlinuz-2.6.22-14-generic root=UUID="string" ro noacpi quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```
Sometimes I have to delete this "quiet" line in order for the load screen not to hang, sometimes I don't - it seems quite random. Is there a cure all fix for this? Can I delete the "quiet" line from the boot file?

Also, do I need that many options to come up, or can I delete everything but the ```
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
```

---

### Post by oli888 on 2008-02-21
The boot sometimes freezes. Apparently, this is because the hard disk isn't sometimes detected.

To solve this, keep trying until you manage to boot. Then open a terminal and run:

```
gksudo gedit /boot/grub/menu.lst
```

Now, look for the first Ubuntu section, and on the line starting with "kernel", add the following to the end.

```
all_generic_ide
```

On the line starting with "title", change the name to "Ubuntu (fixed)", so you know what to choose when rebooting.

Finally, save the file and reboot. You should now always be able to boot, regardless of the partition size.

Good luck,

Oliver

---

