---
title: "cannot mount RCA Lyra mp3 player"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by RyanGT on 2006-01-01
I am trying to use my RCA Lyra 1080B mp3 player in Linux.  I read on the internet somewhere that it is supposed to support ogg files, so I was all excited to try it, but when I plug it in, not much happens. It does show up in Nautilus, but when I right click and select mound I get:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg | tail gives:
[4299556.131000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 16, size 4096)
[4299556.131000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4299556.154000] end_request: I/O error, dev sda, sector 0
[4299556.155000] XFS: SB read failed
[4299556.171000] end_request: I/O error, dev sda, sector 0
[4299556.173000] XFS: SB read failed
[4299556.190000] end_request: I/O error, dev sda, sector 64
[4299556.196000] end_request: I/O error, dev sda, sector 120
[4299556.220000] end_request: I/O error, dev sda, sector 64
[4299556.229000] end_request: I/O error, dev sda, sector 120

And here is more of dmesg:

[4299555.536000] UDF-fs: No partition found (1)
[4299555.559000] end_request: I/O error, dev sda, sector 64
[4299555.567000] end_request: I/O error, dev sda, sector 249340
[4299555.574000] end_request: I/O error, dev sda, sector 248316
[4299555.581000] end_request: I/O error, dev sda, sector 248092
[4299555.593000] end_request: I/O error, dev sda, sector 249332
[4299555.600000] end_request: I/O error, dev sda, sector 248308
[4299555.607000] end_request: I/O error, dev sda, sector 248084
[4299555.614000] end_request: I/O error, dev sda, sector 248740
[4299555.622000] end_request: I/O error, dev sda, sector 247716
[4299555.629000] end_request: I/O error, dev sda, sector 247492
[4299555.636000] end_request: I/O error, dev sda, sector 248732
[4299555.643000] end_request: I/O error, dev sda, sector 247708
[4299555.650000] end_request: I/O error, dev sda, sector 247484
[4299555.657000] end_request: I/O error, dev sda, sector 204596
[4299555.664000] end_request: I/O error, dev sda, sector 203572
[4299555.672000] end_request: I/O error, dev sda, sector 203348
[4299555.679000] end_request: I/O error, dev sda, sector 204588
[4299555.686000] end_request: I/O error, dev sda, sector 203564
[4299555.693000] end_request: I/O error, dev sda, sector 203340
[4299555.699000] end_request: I/O error, dev sda, sector 203996
[4299555.706000] end_request: I/O error, dev sda, sector 202972
[4299555.714000] end_request: I/O error, dev sda, sector 202748
[4299555.722000] end_request: I/O error, dev sda, sector 203988
[4299555.732000] end_request: I/O error, dev sda, sector 202964
[4299555.739000] end_request: I/O error, dev sda, sector 202740
[4299555.746000] end_request: I/O error, dev sda, sector 1248
[4299555.753000] end_request: I/O error, dev sda, sector 1024
[4299555.754000] UDF-fs: No partition found (1)
[4299555.776000] end_request: I/O error, dev sda, sector 64
[4299555.777000] isofs_fill_super: bread failed, dev=sda, iso_blknum=16, block=32
[4299555.799000] end_request: I/O error, dev sda, sector 64
[4299555.800000] isofs_fill_super: bread failed, dev=sda, iso_blknum=16, block=32
[4299555.815000] FAT: utf8 is not a recommended IO charset for FAT filesystems,filesystem will be case sensitive!
[4299555.822000] end_request: I/O error, dev sda, sector 0
[4299555.823000] FAT: unable to read boot sector
[4299555.839000] end_request: I/O error, dev sda, sector 0
[4299555.840000] FAT: unable to read boot sector
[4299555.850000] printk: 1 messages suppressed.
[4299555.850000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4299555.857000] end_request: I/O error, dev sda, sector 0
[4299555.858000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Unable toread primary boot sector.
[4299555.858000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4299555.858000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4299555.881000] end_request: I/O error, dev sda, sector 0
[4299555.882000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Unable toread primary boot sector.
[4299555.882000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4299555.882000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4299555.906000] end_request: I/O error, dev sda, sector 2
[4299555.907000] HFS+-fs: unable to find HFS+ superblock
[4299555.929000] end_request: I/O error, dev sda, sector 2
[4299555.930000] HFS+-fs: unable to find HFS+ superblock
[4299555.956000] end_request: I/O error, dev sda, sector 2
[4299555.957000] VFS: Can't find a HFS filesystem on dev sda.
[4299555.979000] end_request: I/O error, dev sda, sector 2
[4299555.980000] VFS: Can't find a HFS filesystem on dev sda.
[4299556.001000] end_request: I/O error, dev sda, sector 2
[4299556.002000] EXT3-fs: unable to read superblock
[4299556.024000] end_request: I/O error, dev sda, sector 2
[4299556.025000] EXT3-fs: unable to read superblock
[4299556.047000] end_request: I/O error, dev sda, sector 2
[4299556.048000] EXT2-fs: unable to read superblock
[4299556.070000] end_request: I/O error, dev sda, sector 2
[4299556.072000] EXT2-fs: unable to read superblock
[4299556.094000] end_request: I/O error, dev sda, sector 16
[4299556.095000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 2, size 4096)
[4299556.101000] end_request: I/O error, dev sda, sector 128
[4299556.101000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 16, size 4096)
[4299556.101000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not f ind reiserfs on sda
[4299556.124000] end_request: I/O error, dev sda, sector 16
[4299556.125000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 2, size 4096)
[4299556.131000] end_request: I/O error, dev sda, sector 128
[4299556.131000] ReiserFS: sda: warning: sh-2006: read_super_block: bread failed (dev sda, block 16, size 4096)
[4299556.131000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not f ind reiserfs on sda
[4299556.154000] end_request: I/O error, dev sda, sector 0
[4299556.155000] XFS: SB read failed
[4299556.171000] end_request: I/O error, dev sda, sector 0
[4299556.173000] XFS: SB read failed
[4299556.190000] end_request: I/O error, dev sda, sector 64
[4299556.196000] end_request: I/O error, dev sda, sector 120
[4299556.220000] end_request: I/O error, dev sda, sector 64
[4299556.229000] end_request: I/O error, dev sda, sector 120


Can anyone help me with this?

Thanks,

Ryan

---

### Post by lapark on 2006-01-03
It sounds like you have the same problem as me:
[http://www.ubuntuforums.org/showthread.php?t=110893](http://www.ubuntuforums.org/showthread.php?t=110893)

The errors reported show that the filesystem is not detected. It is also strange that there is no /dev/sda1 created (implying that a partition is not found on the device?)

I have read that the cause could be that the kernel is over checking the filesystem and reporting the errors. I am assuming this because my usb mp3 player mounts under windows as having a FAT filesystem and linux should be able to mount FAT filesystems.

Last year I had the same problem with my digital camera when plugged into the usb port. I eventually found a kernel patch that fixed it and allowed it to mount. Hopefully there will be something like this for us when using mp3 players.

Does anyone know of a patch for this behaviour?

---

### Post by lapark on 2006-01-03
I have just found that Microsoft has their own data transfer protocol for music devices called Media Transfer Protocol (MTP), rather than using USB Mass Stoage (UMS). MTP which cannot be implemented in Linux [1]

However, this page suggests that MTP is only used in devices containing hard drives (not flash) [2].

The flash mp3 player I purchased states on the packet that it works with Windows Me,2000,XP, but a driver must be installed for it to mount with Windows 95,98. I suppose this suggests that it doesn't use MTP.

The article [2] mentions a Mass Storage Class (MSC) protocol used with flash devices. Is this the same as UMS?

Is any of this information useful?

[1] [http://gentoo-wiki.com/HOWTO_iRiver#H10:_Starting_UMS_Mode](http://gentoo-wiki.com/HOWTO_iRiver#H10:_Starting_UMS_Mode)
[2] [http://www.directionsonmicrosoft.com/sample/DOMIS/update/2004/10oct/1004mpumsf_sb.htm](http://www.directionsonmicrosoft.com/sample/DOMIS/update/2004/10oct/1004mpumsf_sb.htm)

---

### Post by lapark on 2006-01-03
I found that there is a kernel config option called USB_STORAGE_USBAT in the 2.6.12 kernel that says it supports the RCA LYRA MP3 portable. Try to recompile the kernel with this option enabled and tell me how you go.

---

### Post by RyanGT on 2006-01-04
I am not super excited about recompiling the kernel (I have only tried it once or twice), but it would be really cool if this worked.  I will try this (probably this weekend) and let you know.  Thanks for your help.

Ryan

---

### Post by lapark on 2006-01-04
You could also try installing the 2.6.7 kernel and manually mounting your device. It worked for me. (See [http://www.ubuntuforums.org/showthread.php?t=110893](http://www.ubuntuforums.org/showthread.php?t=110893))

---

### Post by RyanGT on 2006-01-04
I am currently running a 2.6.12 kernel.  Are you suggesting going backward several kernels revisions?

---

### Post by lapark on 2006-01-04
At kernel 2.6.8 there was the inclusion of the usb hotplugging stuff and automatic device creation. This is meant to make hot pluggable devices easier to handle, but it caused alot of problems with usb devices that did not strictly follow the mass storage protocol. 

To test if this is the problem:
* install the kernel 2.6.7 (don't remove 2.6.12), reboot and select the older 2.6.7 using grub.
* plug in the usb mp3 player and check dmesg for detection of the device and any errors (there should be no errors)
* enter the /dev directory and create the sda device using:
> sudo ./MAKEDEV sda
* assuming you have a directory called /media/mp3player and that the mp3 player has a FAT filesystem, try to mount the device using:
> sudo mount -t vfat /dev/sda /media/mp3player

If this does not work, this is not the problem.

---

### Post by RyanGT on 2006-01-04
So how do I install a 2.6.7 kernel?  I can't find it in the package manager.

---

### Post by lapark on 2006-01-04
Good question. I installed mine while I had warty, but it seems that it has been wiped from the face of the earth. The debian repository does not have it either (I only looked for about 5 minues, so I could be wrong).

Try this instead:
[http://packages.debian.org/stable/base/kernel-image-2.4.27-2-686](http://packages.debian.org/stable/base/kernel-image-2.4.27-2-686)

I can't guarantee that it will do the same trick untill I go home and test it out.

---

### Post by lapark on 2006-01-05
Sorry, but I found that my version of the 2.4.27 kernel is compiled without usb storage support (I built it in the days before I had a usb drive). This means that I can't test it for you. Just download the prebuilt kernel and try it, I can't see why it would not work.

---

