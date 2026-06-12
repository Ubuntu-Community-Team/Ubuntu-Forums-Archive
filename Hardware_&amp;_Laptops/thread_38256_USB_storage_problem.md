---
title: "USB storage problem"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by andbert on 2005-05-30
Im on a Fujitsu-Siemens Scenic E, 2,4 ghz, 512 mb ram, with most of the hardware Intel.
Im running Kubuntu 5.04 (i guess)

I have a samsung 160 gig usb-disk, and until recently i have been able to mount it, copy to/from and stream.
After a format and reinstallation of kubuntu, something odd happened.

I am able to mount it, browse it, and use small files...
But f.ex when I try to move lets say a 100 mb mp3 folder to my primary HD it gives me the output "stalled"
Same thing when trying to stream from it.

The USB disk contains 2 partitions, one fat32 (30 gb) and the rest ext3...

my syslog looks like this

```
May 30 23:16:28 localhost kernel: Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
May 30 23:16:28 localhost udev[8179]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '$
May 30 23:16:28 localhost udev[8179]: creating device node '/dev/sda'
May 30 23:16:28 localhost udev[8234]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda1' becomes $
May 30 23:16:28 localhost udev[8234]: creating device node '/dev/sda1'
May 30 23:16:28 localhost udev[8236]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda2' becomes $
May 30 23:16:28 localhost udev[8236]: creating device node '/dev/sda2'
May 30 23:16:38 localhost kernel: UDF-fs: No VRS found
May 30 23:16:38 localhost kernel: UDF-fs: No VRS found
May 30 23:16:38 localhost kernel: Unable to identify CD-ROM format.
May 30 23:16:38 localhost kernel: Unable to identify CD-ROM format.
May 30 23:16:38 localhost kernel: FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case se$
May 30 23:17:01 localhost /USR/SBIN/CRON[8467]: (root) CMD (   run-parts --report /etc/cron.hourly)
May 30 23:17:28 localhost kernel: UDF-fs: No partition found (1)
May 30 23:17:28 localhost kernel: UDF-fs: No partition found (1)
May 30 23:17:28 localhost kernel: Unable to identify CD-ROM format.
May 30 23:17:28 localhost kernel: Unable to identify CD-ROM format.
May 30 23:17:28 localhost kernel: FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case se$
May 30 23:17:28 localhost kernel: FAT: bogus number of reserved sectors
May 30 23:17:28 localhost kernel: VFS: Can't find a valid FAT filesystem on dev sda1.
May 30 23:17:28 localhost kernel: FAT: bogus number of reserved sectors
May 30 23:17:28 localhost kernel: VFS: Can't find a valid FAT filesystem on dev sda1.
May 30 23:17:29 localhost kernel: NTFS driver 2.1.22 [Flags: R/O MODULE].
May 30 23:17:29 localhost kernel: NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please us$
May 30 23:17:29 localhost kernel: NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
May 30 23:17:29 localhost kernel: NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not use$
May 30 23:17:29 localhost kernel: NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
May 30 23:17:29 localhost kernel: NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid. May 30 23:17:29 localhost kernel: NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not use$
May 30 23:17:29 localhost kernel: NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
May 30 23:17:29 localhost kernel: HFS+-fs: unable to find HFS+ superblock
May 30 23:17:29 localhost kernel: HFS+-fs: unable to find HFS+ superblock
May 30 23:17:29 localhost kernel: VFS: Can't find a HFS filesystem on dev sda1.
May 30 23:17:29 localhost kernel: VFS: Can't find a HFS filesystem on dev sda1.
May 30 23:17:29 localhost kernel: EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
May 30 23:17:29 localhost kernel: kjournald starting.  Commit interval 5 seconds
May 30 23:17:29 localhost kernel: EXT3 FS on sda1, internal journal
May 30 23:17:29 localhost kernel: EXT3-fs: recovery complete.
May 30 23:17:29 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
May 30 23:19:23 localhost gconfd (andreas-8567): starting (version 2.10.0), pid 8567 user 'andreas'
May 30 23:19:23 localhost gconfd (andreas-8567): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-o$ May 30 23:19:23 localhost gconfd (andreas-8567): Resolved address "xml:readwrite:/home/andreas/.gconf" to a writable config$
May 30 23:19:23 localhost gconfd (andreas-8567): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-on$
``` 

anyone with a possible solution?

---

### Post by andbert on 2005-05-31
Anyone?

---

### Post by andbert on 2005-05-31
Sorry for bothering you.
I fixed the problem.

It had something to do with the kernel, so i booted with an earlier version, and now everything works fine.

Could this be a bug in the latest kernel or has it something to do with my box?

---

### Post by vincent_a on 2005-06-01
It could be, i have problems with my USB device since i've updated the kernel. How did you boot on your earlier kernel ?

---

### Post by andbert on 2005-06-02
In Grub boot menu, i've got the earlier versions of the kernel.
So just work your way down the list, and find a version.

Not sure how do downgrade if you dont have this option, but i think there are several threads about it on the forum. Use the search-option.

Good luck :)

---

