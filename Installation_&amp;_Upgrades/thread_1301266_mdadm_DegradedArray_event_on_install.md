---
title: "mdadm DegradedArray event on install"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by DrJohn999 on 2009-10-25
Asus M4A78T_E (BIOS 2001), AMD Phenom II X4 945, 4G DDR3 1600, BIOS to defaults, except AHCI on the SATA controller, no OC. Jaunty installed from Alternate AMD-64 iso. Identical WD 340 GB drives at SATA ports 1 & 2 (somehow detected as 1 and 3...). /dev/MD0 configured as RAID1 using /dev/sda1 and /dev/sdc1 as ext4:

/dev/sda5 and /dev/sdc5 are swap partitions, 6.1 GB apiece.

System boots OK, but in syslog I find these:

```
Oct 25 17:30:26 M4A78 kernel: [    5.721555] raid1: raid set md0 active with 1 out of 2 mirrors
Oct 25 17:30:26 M4A78 kernel: [    5.722153]  md0: unknown partition table

Oct 25 17:30:27 M4A78 mdadm[3164]: DegradedArray event detected on md device /dev/md0

```

Yet:

```
~$ sudo dmraid -r
/dev/sdc: isw, "isw_dfcgcjecbg", GROUP, ok, 293046766 sectors, data@ 0
/dev/sda: isw, "isw_dfcgcjecbg", GROUP, ok, 293046766 sectors, data@ 0

```

Is the 'degraded' event just due to initial mirroring? I'm hesitating to install any new packages until this is resolved.

Thanks,  DrJohn

---

### Post by DrJohn999 on 2009-10-26
Repartitioned and reformatted (to EXT3 this time) but still the same result; there's something about the partition table that mdadm doesn't like.

Clearly, the partition tool that's part of the alternate install CD isn't actually reinitializing the partition tables on the drives when I 'delete' the RAID and SWAP partitions there. These two drives were in use previously (before the MB upgrade) by FakeRAID on the previous mobo. I think it's probably the source of this problem. As I said earlier, the H/W SATA / RAID controller on the new board is set for ACPI not RAID.

Can anyone provide a hint or better on how to completely wipe these drives' partition tables and thereby start with a truly blank slate?

Thanks

---

