---
title: "Botched Ubuntu install with Raid1"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by eyefragment on 2009-01-09
Hi all,

I recently attempted to install Linux on a machine configured with Raid 1 using intel software raid (isw).  Big mistake?  In any case, after rebooting, Grub gives me an Error 21 (Disk not found).  Googling then revealed that I needed to make some modifications to the usual install process.  In particular, I've followed the instructions on this link ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)).

The first step is installing and using dmraid.  However, when I try to activate my array through dmraid, I am given

```

ubuntu@ubuntu:/media$ sudo dmraid -ay
ERROR: isw: unsupported map state 0x2 on /dev/sdb for Main_System
ERROR: adding /dev/sdb to RAID set "isw_cdaedadada"
ERROR: removing RAID set "isw_cdaedadada"
ERROR: isw: unsupported map state 0x2 on /dev/sda for Main_System
ERROR: adding /dev/sda to RAID set "isw_cdaedadada"
ERROR: removing RAID set "isw_cdaedadada"
```

Googling more seems to suggest that I have a degraded raid setup (anyone know how I can tell?  I do not know what degraded raid is), and cannot successfully install ubuntu with my setup at all, but I figured I would post here to see if anyone knew of a workaround.  Here's all of the relevant info that I can think of:

```

sudo dmraid -r
/dev/sdb: isw, "isw_cdaedadada", GROUP, ok, 781422765 sectors, data@ 0
/dev/sda: isw, "isw_cdaedadada", GROUP, ok, 586072365 sectors, data@ 0

```

```
ubuntu@ubuntu:/media$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbccabcca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36479   293017536    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbccabcca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36479   293017536    7  HPFS/NTFS

```

Additionally, just repairing my system to be able to access windows again would be great.  However, I cannot find where grub is installed (locate grub shows no matches outside of the liveCD, and running grub then running find /boot/grub/stage1 gave no matches), nor am I sure exactly what I would need to change my grub.lst to in order to set this up.

To further complicate things, my USB ports do not start up until ubuntu is fully loaded, so I cannot use the alternate installer, or the windows reinstall disk, for example.  I will have a non-usb keyboard in a few days to work around this issue, but I would like to get my system running sooner than that if possible.

If you've got any suggestions, I'd greatly appreciate it. Thanks in advance!

---

