---
title: "ntfs raid mounting issue"
date: 2008-07-20
forum: General Help
---

### Post by dottedquad on 2008-07-20
[SIZE="4"]**dmariad -r out-puts:**[/SIZE]

/dev/sdb: sil, "sil_ahbiejbgcgaf", stripe, ok, 312579712 sectors, data@ 0
/dev/sda: sil, "sil_ahbiejbgcgaf", stripe, ok, 312579712 sectors, data@ 0

[SIZE="4"][B]
ntfs-3g /dev/mapper/sil_ahbiejbgcgaf /mnt/windows out-puts:[/B][/SIZE]

NTFS signature is missing.
Failed to mount '/dev/mapper/sil_ahbiejbgcgaf': Invalid argument
The device '/dev/mapper/sil_ahbiejbgcgaf' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
[B][SIZE="4"]
fdisk -l outputs:[/SIZE][/B]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bc63e26

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312576673+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6041488d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9541    76638051   83  Linux
/dev/sdc2            9542        9729     1510110    5  Extended
/dev/sdc5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/dm-0: 320.0 GB, 320081625088 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bc63e26

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       38914   312576673+   7  HPFS/NTFS

Disk /dev/dm-1: 320.0 GB, 320078513664 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


I believe ntfs-3g /dev/mapper/sil_ahbiejbgcgaf /mnt/windows is the command I used when I was using Kubuntu and now that I switch to regular ubuntu I'm having this issue.  I appreciate the help in advanced :-)

-Rich

---

### Post by dottedquad on 2008-07-20
Well, It was a typo error with my command

ntfs-3g /dev/mapper/sil_ahbiejbgcgaf1 /mnt/windows is the right command where it says sil_ahbiejbgcgaf1 i wrote sil_ahbiejbgcgafl

-Thanks,
    Rich

---

### Post by fjgaude on 2008-07-20
You can auto mount the volume on boot up if you placed this line in your /etc/fstab file, at least I think so:

```
/dev/mapper/sil_ahbiejbgcgaf1 /mnt/windows ntfs-3g defaults 0 0
```

Glad you only issue was a typo.

---

