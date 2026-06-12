---
title: "Add vista to grub on drive sdb1"
date: 2008-11-06
forum: General Help
---

### Post by gellpak on 2008-11-06
So I've done quite a bit of searching and tried to figure this out myself already- I just installed 8.10 alongside vista (on separate hard drives), but grub didn't update itself during the install to include my existing windows install as it did the last time I tried this.

So I want to get back into windows, but I don't know how to set up grub for this. Right now, I've figured out that my vista drive is sdb1, and translated this to this code in menu.lst:

```

title 		Windows
root 		(hd1,0)
savedefault
makeactive
chainloader +1

```

I've also tried (sd1,0)... no luck.

With (hd1,0) I get a bootldr is not installed error, which I suppose could be a windows thing but the ubuntu install shouldn't have touched that drive, and all the directory structure is intact. Anyone know what's up?

---

### Post by geirha on 2008-11-06
Try with (hd1) instead of (hd1,0)

---

### Post by gellpak on 2008-11-06
Error 12: Invalid device requested

---

### Post by geirha on 2008-11-06
Hm, try with 
```
rootnoverify (hd1,0)
``` 
instead of 
```
root (hd1,0)
```

---

### Post by TeXtonyx on 2008-11-06
Maybe the "map" function is needed. The Vista entry is the last one.

I've copied and pasted the more relevant portions of my hd1 menu.lst
I have XP + Ubuntu on drive 0 = sda
I have Vista + Ubuntu on drive 1 = sdb

I installed grub to the /boot partition not MBR on both drives.
So Ubuntu on drive 0, (hd0,4) = sda5
And Ubuntu on drive 1, (hd1,4) = sdb5

Notice that XP on sda1 has a simple grub entry:
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
chainloader    +1

--------------------------------------------

But that Vista on sdb1, like in your case, has a more complex entry:
# on /dev/sdb1
title        Windows Vista/Longhorn (loader)
root        (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


TeX: I didn't notice this more detailed configuration (above) posted/offered.
I'm messing around with Easybcd for dual booting and my general impression
is that it works better to have Windows on the first drive and Ubuntu on
the second drive. I'm not sure that switching the cables and jumper settings
on your system will easily accomplish this without complications. IDE or SATA?


title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=c8c03fed-20dd-4169-b4ab-361eb60f748d ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

## ## End Default Options ##

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=c8c03fed-20dd-4169-b4ab-361eb60f748d ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=22e06212-2963-4aee-aac3-d9edeeefcea7 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista/Longhorn (loader)
root        (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

