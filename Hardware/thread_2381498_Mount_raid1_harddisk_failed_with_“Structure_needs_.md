---
title: "Mount raid1 harddisk failed with “Structure needs cleaning”"
date: 2018-01-01
forum: Hardware
---

### Post by tarekff on 2018-01-01
[COLOR=#000000][FONT=Verdana]When i try to mount a xfs harddisk that was a part of linux raid1, i got the following error message[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]mount: mount /dev/md4 on /mnt/usbhdd1 failed: Structure needs cleaning[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I tried exam the harddisk using mdadm --examine, i got the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]mdadm: No md superblock detected on /dev/md4[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]when i execute sudo fdisk -l /dev/md4, i got[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Disk /dev/md4: 928.4 GiB, 996889951232 bytes, 1947050686 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What can i do to mount this harddisk successfully?[/FONT][/COLOR]

---

### Post by SeijiSensei on 2018-01-02
That error arises when the XFS file system fails the consistency check. Like with Windows chkdsk or fsck for ext filesystems you need to run the equivalent xfs_check program from the xfsprogs package. [http://manpages.ubuntu.com/manpages/trusty/man8/xfs_check.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/xfs_check.8.html)

Whether this will work on half a RAID1 array I don't know. I have been able to mount one half of an array formatted with ext4. I had bad experiences with losing data with XFS after power outages. These days I avoid XFS in favor of ext4.

---

