---
title: "Windows won't boot from GRUB Error 25: Disk Read error"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Morphus on 2009-03-05
[SOLVED]This issue has been resolved.
The problem was despite device.map showing the devices were mapped to (hd0), (hd1) and (hd2) they were infact mapped to (hd0), (hd2) and (hd3) which became apparent when running the geometry command at the grub CLI. This explains the unable to read disk error as there was no disk mapped to (hd1) though i still have no idea why the device.map and actual mappings were inconsistent.

Hi,

I am having difficulty configuring windows to work correctly with grub and am currently getting Error 25: Disk Read error.
I have 3 HDD's all with NTFS partitions on them, one is bootable with XP on it and another has at the start also has ubuntu and swap partitions on it.

I have only today installed ubuntu and with it grub, and as a result placed the ubuntu drive into the first sata port, with xp in the second port and the 3rd disk in the 3rd port. I deliberately set it up like this as I did not want place grub near the XP disk, for risk of it causing problems when i later install vista.

My problem is that while ubuntu boots nicely, XP will not boot at all, citing Error 25: Disk Read error. At this point it halts, and pressing any key takes me back to grub. I know however there is nothing wrong with the XP disk, as when I remove sata0, XP (sata1) boots fine.

My configuration is as follows:

Ubuntu 8.10

menu.lst:

```
## ## End Default Options ##

# This entry automatically added by the Debian installer for Windows XP on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro  single
```

(continues with other linux versions)

/sbin/fdisk -l :

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd231b932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2112    16964608+  83  Linux
/dev/sda2            2113       30400   227223360    f  W95 Ext'd (LBA)
/dev/sda5            2612       30400   223215111    6  FAT16
/dev/sda6            2114        2611     4000153+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30393   244131741    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf088f46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2612       91201   711599175    f  W95 Ext'd (LBA)
/dev/sdc5            2612       91201   711599143+   7  HPFS/NTFS
```

device.map:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

Edit:

boot.ini:

```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

If anyone knows what I need to do to fix the bootloader that would be great, its not mission critical as I can boot windows w/o the linux drive then hotplug it to get it in windows, though it would be really nice to get it working properly.

---

### Post by zwdev on 2009-03-05
try this and tell us how it goes;

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

---

### Post by Brandon.Viking on 2009-03-05
posted initially without reading your fdisk dump hope the previous post with the chainloader command helps.

---

### Post by Morphus on 2009-03-05
Didn't help. Still unable to read the disk.

This is what the boot.ini looks like:

```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by Morphus on 2009-03-05
I initially modified my menu.lst before attempting to boot windows XP from it as I wanted it as the first boot device, I have since then tested the original file, which I made a backup of. This failed in the same way. For reference here is menu.lst as created by the 8.10 Ubuntu installer:

```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a17ea2cb-ab71-408a-9503-0035bc50e958 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a17ea2cb-ab71-408a-9503-0035bc50e958 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a17ea2cb-ab71-408a-9503-0035bc50e958 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a17ea2cb-ab71-408a-9503-0035bc50e958 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Note, the partition referenced on the third boot device has since been removed, this was an old version of ubuntu 6 or 7 i no longer wanted.

---

### Post by Morphus on 2009-03-05
I have since tried manually editing the menu.lst to other values of drives, partitions. Combinations tried are (hd1,1) (hd1,10) which are both partitions which don't exist. I also tried (hd3,0) which is a SATA port which exists though is disbled with no connected device, this also gave the same error. I tried hd(4,0) which would be a 5th SATA port, which my machine does not have, this gave a different error.

It would seem that I am getting the same error as you would get if you specified a hdd or partition which does not exist, or does not have a boot sector. Hopefully this might help people in locating the problem I'm facing.

Thanks again

---

### Post by Morphus on 2009-03-06
Bumping,

If anyone knows a more appropriate place to post this let me know.

---

### Post by Morphus on 2009-03-06
Updated main post, bump.

---

### Post by Morphus on 2009-03-08
Bump again.

---

