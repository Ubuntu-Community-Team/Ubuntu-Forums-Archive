---
title: "problems with auto mount a USB NTFS disk"
date: 2004-12-08
forum: Hardware &amp; Laptops
---

### Post by orestis82 on 2004-12-08
I can mount the disk correctly, using the fstab file.
I can view the disk correctly (correct permissions)

However, when hot-plugging, the log shows that is detected correctly, but it only scans the disk for all the filesystems except NTFS, and then nothing happens. Is this fixable ?

Running warty 4.10

---

### Post by orestis82 on 2004-12-09
It seems that after I added the fstab line (and rebooted ? not sure), the disk is auto-mounted properly.

---

### Post by piedamaro on 2004-12-28
Very bad. Adding a line to fstab screws up the gnome-volume-manager magic.

Does anyone have a _real_ solution? I.e. ntfs removable drive being automounted?
As orestis said, "However, when hot-plugging, the log shows that is detected correctly, but it only scans the disk for all the filesystems except NTFS, and then nothing happens."

It seems to me it's trying to mount the filesystem as XFS (or hpfs), and obviously fails.

In fedora3 I have ntfs volumes automounted, but I also have ntfs built-in.
The fact is that using stock fedora kernels (with ntfs build as a module), the ntfs automounting works like a charm.

This is the ultimate issue I'm having with ubuntu. :)

---

### Post by piedamaro on 2004-12-28
*bump*

---

### Post by diebels on 2004-12-28
tried loading the ntfs module?

---

### Post by piedamaro on 2004-12-30
As we sad: "I can mount the disk correctly, using the fstab file. I can view the disk correctly (correct permissions)"

When I plug an ntfs usb disk, I have this in log/messages:

Dec 21 19:44:22 ubuntu kernel: usb 1-1: new full speed USB device using address 22
Dec 21 19:44:22 ubuntu kernel: scsi19 : SCSI emulation for USB Mass Storage devi ces
Dec 21 19:44:22 ubuntu kernel: Vendor: Model: Rev:
Dec 21 19:44:22 ubuntu kernel: Type: Direct-Access ANSI SCSI revision: 02
Dec 21 19:44:22 ubuntu kernel: SCSI device sda: 31263 512-byte hdwr sectors (16 MB)
Dec 21 19:44:22 ubuntu kernel: sda: Write Protect is off
Dec 21 19:44:22 ubuntu kernel: /dev/scsi/host19/bus0/target0/lun0: p1
Dec 21 19:44:22 ubuntu kernel: Attached scsi removable disk sda at scsi19, chann el 0, id 0, lun 0
Dec 21 19:44:22 ubuntu scsi.agent[8546]: disk at /devices/pci0000:00/0000:00:03. 0/usb1/1-1/1-1:1.0/host19/19:0:0:0
Dec 21 19:44:22 ubuntu usb.agent[8530]: usb-storage: already loaded
Dec 21 19:44:23 ubuntu kernel: VFS: Can't find a valid FAT filesystem on dev sda 1.
Dec 21 19:44:23 ubuntu kernel: UDF-fs: No partition found (1)
Dec 21 19:44:24 ubuntu kernel: Unable to identify CD-ROM format.
Dec 21 19:44:24 ubuntu kernel: HFS+-fs: unable to find HFS+ superblock
Dec 21 19:44:24 ubuntu kernel: VFS: Can't find a HFS filesystem on dev sda1.
Dec 21 19:44:24 ubuntu kernel: VFS: Can't find ext2 filesystem on dev sda1.
Dec 21 19:44:24 ubuntu kernel: ReiserFS: sda1: warning: sh-2021: reiserfs_fill_s uper: can not find reiserfs on sda1
Dec 21 19:44:24 ubuntu kernel: XFS: bad magic number
Dec 21 19:44:24 ubuntu kernel: XFS: SB validate failed

The question is: why the kernel is trying to use all possible filesystem but ntfs?
Mounting manually it's not an option cause when I plug other devices (for ex. a vfat mp3 player which is being recognized and auto-mounted perfectly), the device node changes from sda to sdb etc.

Does anyone has any clue? Recompiling the kernel with builtin ntfs could help?
*BUMP*

---

### Post by piedamaro on 2005-01-03
*bump*

---

### Post by piedamaro on 2005-01-06
*bump*

---

