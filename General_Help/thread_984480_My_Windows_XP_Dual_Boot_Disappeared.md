---
title: "My Windows XP Dual Boot Disappeared"
date: 2008-11-16
forum: General Help
---

### Post by Cameron462 on 2008-11-16
After my most recent update, my dual boot menu doesn't list XP. 

I saw another thread with a similar problem, and they asked for the results of <sudo fdisk -l>, so here that is:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             766       12160    91530337+   7  HPFS/NTFS
/dev/sda2   *           1         765     6144831   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000ff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32

I'm quite a noob at this kind of thing, so any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-11-16
OK, how about opening a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end, add:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know how it goes. :)

---

### Post by Cameron462 on 2008-11-16
At the end of that menu.lst there is already this:

```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Do I still add that?

---

### Post by caljohnsmith on 2008-11-16
No need to add the entry I gave since you all ready have one that should work. Do you have the "hiddenmenu" line in menu.lst commented? Like:
```
#hiddenmenu
```
If not, I would comment it like above so you get the Grub menu on start up. What exactly do you see on start up? You should see in your Grub menu the option to boot Windows XP since you have an entry in your menu.lst.

---

