---
title: "Disk errors on boot / mount (copied to hardware)"
date: 2013-11-18
forum: Hardware
---

### Post by ottadini on 2013-11-18
I seem to be having some problems with my drives not shutting down cleanly. Can someone help me identify and fix the problem?

The error message I can see in dmesg is:
```
ben@brick:~$ dmesg | grep sda2
[    1.386862]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.993955] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    2.994069] EXT4-fs (sda2): write access will be enabled during recovery
[   20.213091] EXT4-fs (sda2): recovery complete
[   20.229613] EXT4-fs (sda2): mounted filesystem with writeback data mode. Opts: (null)
[   35.018148] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
```

Noting that sda2 is my / (root). 

Symptoms include very occasional boot and OS load problems (system freezing  during boot, or on loading desktop), disk errors showing in some logs (inodes being  deleted):
```
Oct 23 08:04:36 brick kernel: [    2.817994] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
Oct 23 08:04:36 brick kernel: [    2.818115] EXT4-fs (sda2): write access will be enabled during recovery
Oct 23 08:04:36 brick kernel: [    3.094047] EXT4-fs (sda2): orphan cleanup on readonly fs
Oct 23 08:04:36 brick kernel: [    3.123264] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 528801
Oct 23 08:04:36 brick kernel: [    3.127215] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 791772
Oct 23 08:04:36 brick kernel: [    3.127296] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 791770
Oct 23 08:04:36 brick kernel: [    3.127348] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 791705
Oct 23 08:04:36 brick kernel: [    3.175285] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788952
Oct 23 08:04:36 brick kernel: [    3.175320] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788899
Oct 23 08:04:36 brick kernel: [    3.184290] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788451
Oct 23 08:04:36 brick kernel: [    3.184322] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788437
Oct 23 08:04:36 brick kernel: [    3.184350] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788270
Oct 23 08:04:36 brick kernel: [    3.184373] EXT4-fs (sda2): 9 orphan inodes deleted
Oct 23 08:04:36 brick kernel: [    3.184414] EXT4-fs (sda2): recovery complete
Oct 23 08:04:36 brick kernel: [    3.246300] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
```

my /etc/fstab is:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda2 during installation
# /boot was on /dev/sda1 during installation
# /home was on /dev/sda6 during installation
# swap was on /dev/sda5 during installation

UUID=e7972335-1344-4ff8-b4cf-e4b70d2cb8cd /               ext4    errors=remount-ro 0       1
UUID=959fa271-d1d1-4eef-ba14-30e2837a6eea /boot           ext4    defaults        0       2
UUID=c1f3c3f6-5999-4357-8142-c747ed8beb15 /home           ext4    defaults        0       2
UUID=d28d2d75-fc02-41b1-be8e-5a8fa2011e35 none            swap    sw              0       0

# dingo (/dev/sdc1) is the 2TB drive
UUID=003ABB1739377B81  /mnt/dingo  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,locale=en_AU.utf8  0  0

# data is /dev/sdb8
UUID=146FA9B0B6A44D89  /mnt/data  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,locale=en_AU.utf8  0  0
```

I also see (on screen) some words to the effect that unmounting is  throwing an error... but I have no idea where to see that in logs.

---

