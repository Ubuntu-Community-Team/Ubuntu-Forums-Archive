---
title: "Ubuntu/Windows 2000 dual boot problem"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Kugerfang on 2009-06-21
Hello again to all!

I seem to have a problem with the GRUB bootloader. I installed Win2K (XP crashes on installation) on one of my partitions but I have to manually set my BIOS to boot from "IDE0" everytime I want to boot it. Is there anyway to add a new entry to GRUB to boot Windows?

P.S. Ubuntu was installed first.

Since I was browsing other topics and people for asking for the output of "sudo fdisk -l" here it is:

```
Disk /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01cd01cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1244     9992398+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14e614e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9801    78726501   83  Linux
/dev/sdb2            9802        9964     1309297+   5  Extended
/dev/sdb5            9802        9964     1309266   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1357     7783940    b  W95 FAT32

```

Any and all help is welcome. :D

---

### Post by merlinus on 2009-06-21
What is the boot order of your hdds in bios?

Also, post results of:

```

cat /boot/grub/menu.lst

```

---

### Post by Kugerfang on 2009-06-22
The order is as follows:

1) USB
2) CD-ROM
3) IDE1 (Ubuntu)

Like I said, IDE0 is Windows.

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6f3942c5-d10c-402c-8e49-842579166f8a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f3942c5-d10c-402c-8e49-842579166f8a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6f3942c5-d10c-402c-8e49-842579166f8a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f3942c5-d10c-402c-8e49-842579166f8a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6f3942c5-d10c-402c-8e49-842579166f8a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6f3942c5-d10c-402c-8e49-842579166f8a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6f3942c5-d10c-402c-8e49-842579166f8a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6f3942c5-d10c-402c-8e49-842579166f8a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6f3942c5-d10c-402c-8e49-842579166f8a
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

Please note that my previous OS before Ubuntu was XP and it doesn't work anymore.

---

### Post by swerdna on 2009-06-22
Maybe hd(0,0) is reversed. Try this and see what happens:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
    map (hd1) (hd0)
    map (hd0) (hd1)
root		(hd0,0)
#savedefault
chainloader	+1
```

---

### Post by Kugerfang on 2009-06-22
Here's what I put in:

```

title		Microsoft Windows 2000
rootnoverify    (hd0,4)
savedefault
chainloader	+1
```

Please note that I installed Win2000 on a FAT32 10GB partition. Ubuntu can browse that partition fine.

Upon trying to boot using those settings, GRUB gave me this error:

[CENTER]>  Grub Error 13: "Invalid or unsupported executable format"  [/CENTER]

Swerdna's advice also gives the same error.

Also, I think it's possible to edit Win2K's boot.ini file to include Ubuntu.... but I don't know how....

---

### Post by swerdna on 2009-06-22
This will show you how to boot Linux from windows bootloader. It's for openSUSE, but it's a generic thing, not dependent on the distro:
[HowTo Boot / Multiboot openSUSE and Windows (2000, XP, Vista - any mix) using the Windows bootloader]("http://opensuse.swerdna.org/suseboot1.html")

But it's intricate and maybe a last resort if you can't get Grub going.

---

### Post by Kugerfang on 2009-06-24
I just came to a realization.... why am I dual-booting Win2K and Ubuntu when there's a much better gaming PC with XP just 4 meters away?

---

### Post by presence1960 on 2009-06-24
> **Kugerfang said:**
> Here's what I put in:

```

title		Microsoft Windows 2000
rootnoverify    (hd0,4)
savedefault
chainloader	+1
```

Please note that I installed Win2000 on a FAT32 10GB partition. Ubuntu can browse that partition fine.

Upon trying to boot using those settings, GRUB gave me this error:

[CENTER][/CENTER]

Swerdna's advice also gives the same error.



Also, I think it's possible to edit Win2K's boot.ini file to include Ubuntu.... but I don't know how....

you need the map lines in there and there is no (hd0,4) according to your sudo fdisk output. your windows disk has one partition. so either (hd0,0) or (hd1,0) is what you need and the map lines are required also. depending on your boot order in BIOS will determine whether you need to use (hd0,0) or (hd1,0) try this:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

if that doesn't work try (hd1,0)

---

### Post by Kugerfang on 2009-06-24
Still doesn't work. Error 13.

---

