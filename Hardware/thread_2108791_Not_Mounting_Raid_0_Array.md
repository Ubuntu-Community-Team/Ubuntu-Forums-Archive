---
title: "Not Mounting Raid 0 Array"
date: 2013-01-25
forum: Hardware
---

### Post by gamertyke on 2013-01-25
So here's the senario, I have a 64GB SSD with 2 partitions, one for Windows, and one for Ubuntu 12.10. All my data is stored on a RAID 0 (relax, it's backed up somewhere else too). At first, Ubuntu wasn't even detecting it, so I did some poking around and was told to try "sudo dmraid -ay" which results in this:

```
mike@mike-OEM:~$ sudo dmraid -ay
RAID set "isw_bgjjdcedeb_WD 1.0TB RAID0" already active
ERROR: opening "/dev/mapper/isw_bgjjdcedeb_WD 1.0TB RAID0"
```

But now the drive detects in the file explorer. I go and click on it and get this:

```
Error mounting /dev/dm-1 at /media/mike/Mike's ****: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/dm-1" "/media/mike/Mike's ****"' exited with non-zero exit status 21: fuse: mount failed: No such file or directory
```

Any help would be greatly appreciated. Thanks in advance.

---

### Post by ronparent on 2013-01-28
If a bios based RAID, what is the status of the RAID set in the RAID bios on boot? Are the /dev/mapper symbolic links present after boot? If the RAID at least appears functional in the RAID bios look in the udev log for errors.

---

