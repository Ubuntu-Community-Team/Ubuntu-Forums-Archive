---
title: "fakeRaid, 965P-DS3 and problems"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by quilty on 2008-01-26
Hello,

I'm running Kubuntu 7.10 since a few hours and everything works perfectly but the access to my raid-1 I used to have when running Windows. The OS itself runs on a "normal" SATA drive connected to the Intel SATA controller. The two raid drives are connected to one of those "fake" onboard raid-controllers in mirrored mode. So I won't have problems messing around with grub and the boot configuration.

I followed the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") and noticed following message when running "sudo dmraid -ay":
```
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "jmicron" formats discovered (using jmicron)!
ERROR: sil: only 3/4 metadata areas found on /dev/sdc, electing...
/dev/sdc: "sil" and "jmicron" formats discovered (using jmicron)!
```
I googled the error message and didn't really find a solution for the problem but for now I don't care about it. As you can see my raid set is found but it's name is strange: jmicron_GRAID followed by allot of spaces.
```
~$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 63 2008-01-26 15:08 control
brw-rw---- 1 root disk 254,  0 2008-01-26 15:08 jmicron_GRAID           ?
```
The problem now is that I'm not sure how to mount the partitions on the raid now since they are named the same as fdisk shows:
```
~$ sudo fdisk -l /dev/mapper/jmicron_GRAID\ \ \ \ \ \ \ \ \ \ \ ^A

Disk /dev/mapper/jmicron_GRAID           : 400.0 GB, 400069492736 bytes
255 heads, 63 sectors/track, 48639 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45664951

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/jmicron_GRAID           1   *           1       10199    81923436    7  HPFS/NTFS
/dev/mapper/jmicron_GRAID           2           10200       22947   102398310    7  HPFS/NTFS
/dev/mapper/jmicron_GRAID           3           22948       48638   206362957+   7  HPFS/NTFS
```

Any ideas where I should start fixing the problem or anyone found a solution to run a Raid-1 on a Gigabyte GA-965P-DS3 using the internal raid controller?

quilty

---

### Post by quilty on 2008-01-30
Just to let everybody know - there is no fix for this problem available yet.

Even with dmraid manually updated to rc14 it won't work. With dmraid-1.0.0.rc15 there should be a fix available - at least the developer announced it on the redhat board.

quilty

---

