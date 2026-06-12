---
title: "problem with partition manager"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by NO2 on 2009-01-25
i was previously using ubuntu x64 and windows xp
i tried pcbsd which removed my c drive(windows).
i used the live cd and formatted sda1 to fat32.
i had sda8 as ext3 and sda9 as swap but ihad to change their sizes so sda8 became swap and sda9 ext3.
i installed xp again to sda1.
i used the live cd, but now the partition manager was showing my hard disk as unallocated, showing no partitions at all.
what could be the problem?

---

### Post by Partyboi2 on 2009-01-25
Can you boot the live cd and open a terminal (Applications>Accessoires>Terminal) and post the output to
```
sudo fdisk -l
```

---

### Post by caljohnsmith on 2009-01-25
Often when the partition editor shows your entire drive as unallocated, that's a sign that the HDD's partition table is corrupt. In order to check, please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
Be sure to include the "u" option with fdisk so I can see the start/stop points as sectors, not cylinders.

---

### Post by NO2 on 2009-01-26
ubuntu@ubuntu:~$ su
Password: 
root@ubuntu:/home/ubuntu# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1244     9992398+   b  W95 FAT32
/dev/sda2            1245        9728    68147730    f  W95 Ext'd (LBA)
/dev/sda3            2551        5100    20482843+   b  W95 FAT32
/dev/sda5            1245        1505     2096419+  82  Linux swap / Solaris
/dev/sda6            1506        2550     8393931   83  Linux
/dev/sda7            5101        7650    20482843+   b  W95 FAT32
/dev/sda8            7651        9728    16691503+   b  W95 FAT32
root@ubuntu:/home/ubuntu# fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19984859     9992398+   b  W95 FAT32
/dev/sda2        19984860   156280319    68147730    f  W95 Ext'd (LBA)
/dev/sda3        40965813    81931499    20482843+   b  W95 FAT32
/dev/sda5        19984986    24177824     2096419+  82  Linux swap / Solaris
/dev/sda6        24177888    40965749     8393931   83  Linux
/dev/sda7        81931563   122897249    20482843+   b  W95 FAT32
/dev/sda8       122897313   156280319    16691503+   b  W95 FAT32
root@ubuntu:/home/ubuntu# sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 19984797, Id= b, bootable
/dev/sda2 : start= 19984860, size=136295460, Id= f
/dev/sda3 : start= 40965813, size= 40965687, Id= b
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 19984986, size=  4192839, Id=82
/dev/sda6 : start= 24177888, size= 16787862, Id=83
/dev/sda7 : start= 81931563, size= 40965687, Id= b
/dev/sda8 : start=122897313, size= 33383007, Id= b

---

### Post by caljohnsmith on 2009-01-26
> **NO2 said:**
> 
```
root@ubuntu:/home/ubuntu# fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19984859     9992398+   b  W95 FAT32
[COLOR="Red"]/dev/sda2        19984860   156280319[/COLOR]    68147730    f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sda3        40965813    81931499[/COLOR]    20482843+   b  W95 FAT32
/dev/sda5        19984986    24177824     2096419+  82  Linux swap / Solaris
/dev/sda6        24177888    40965749     8393931   83  Linux
/dev/sda7        81931563   122897249    20482843+   b  W95 FAT32
/dev/sda8       122897313   156280319    16691503+   b  W95 FAT32

```

Unfortunately your partition table is corrupt; right now your sda3 primary partition is inside of your sda2 extended partition, so sda3 should be a logical partition instead. Fortunately it doesn't look like the problem will be difficult to correct, so how about first downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. In case anyone is interested, for convenience here is the contents of the partition_table.txt file:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 19984797, Id= b, bootable
/dev/sda2 : start= 19984860, size=136295460, Id= f
[COLOR="Blue"]/dev/sda3 : start=        0, size=        0, Id= 0[/COLOR]
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 19984986, size=  4192839, Id=82
/dev/sda6 : start= 24177888, size= 16787862, Id=83
[COLOR="Blue"]/dev/sda7 : start= 40965813, size= 40965687, Id= b[/COLOR]
/dev/sda8 : start= 81931563, size= 40965687, Id= b
/dev/sda9 : start=122897313, size= 33383007, Id= b

```
So basically all I did was move primary partition sda3 so it will become logical partition sda7, and then delete sda3 by zeroing all its fields. Fortunately all the logical partitions have free sectors between them where the EBRs (Extended Boot Records) can reside, so it is not necessary to resize any of the partitions to accommodate the partition change. Next reboot, and please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
And we can work from there.

---

### Post by NO2 on 2009-01-26
gparted is detecting the partitions now.
Thank You very much caljohnsmith.

---

### Post by caljohnsmith on 2009-01-26
Glad that worked OK; cheers and have fun with Ubuntu.

---

