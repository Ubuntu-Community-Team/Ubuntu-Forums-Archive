---
title: "Can't format a pendrive to NTFS"
date: 2019-04-22
forum: Hardware
---

### Post by lutty2029 on 2019-04-22
So, I am trying to return to Windows 7 (mostly because of my mom), and I just can't do it. I have the iso, a bank pendrive, Gparted and WoeUSB, so I try to format it to NTFS (needed because of the iso's size), but it says this:

```
ntfs_mst_post_read_fixup_warn: magic: 0xffff00fc  size: 1024   usa_ofs: 56564  usa_count: 2713: Invalid argumentntfs_mst_post_read_fixup_warn: magic: 0xfdff00fc  size: 1024   usa_ofs: 38978  usa_count: 2111: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xfffe00fc  size: 1024   usa_ofs: 36822  usa_count: 2712: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xfdfe00fc  size: 1024   usa_ofs: 52064  usa_count: 2110: Invalid argument
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdf1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.


Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs.
```

What do I do?

---

### Post by yancek on 2019-04-22
> Failed to mount '/dev/sdf1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!

That generally means the filesystem on the partition on the drive in question was attached to a windows filesystem which was hibernated.  Either that or the filesystem is messed up and needs chkdsk.  Do you have any windows OS?  Is there any data on the usb?  If no data, use GParted to create a new partition table on the device.

> The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs

Do you have the above software installed on your Linux OS?

---

