---
title: "problems with mounting"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by myha on 2006-02-15
Hello!

I have a problem with mounting USB flashdrive...

When I insert it everything is ok, I can see the devide in Computer.....
Here is dmesg upon insertion:
```
[4297171.115000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4297171.212000] scsi1 : SCSI emulation for USB Mass Storage devices
[4297171.214000] usb-storage: device found at 4
[4297171.214000] usb-storage: waiting for device to settle before scanning
[4297176.217000]   Vendor: LEXAR     Model: JUMPDRIVE ELITE   Rev: 1000
[4297176.217000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4297176.230000] SCSI device sda: 502880 512-byte hdwr sectors (257 MB)
[4297176.233000] sda: Write Protect is off
[4297176.233000] sda: Mode Sense: 43 00 00 00
[4297176.233000] sda: assuming drive cache: write through
[4297176.247000] SCSI device sda: 502880 512-byte hdwr sectors (257 MB)
[4297176.249000] sda: Write Protect is off
[4297176.249000] sda: Mode Sense: 43 00 00 00
[4297176.249000] sda: assuming drive cache: write through
[4297176.249000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4297176.366000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[4297176.467000] usb-storage: device scan complete

```

But when I try to mount it I get the following error:
```
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

```

And the output from dmesg:
```
[4297147.209000] UDF-fs: No partition found (1)
[4297147.325000] UDF-fs: No partition found (1)
[4297147.584000] Unable to identify CD-ROM format.
[4297147.845000] Unable to identify CD-ROM format.
[4297147.999000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4297148.002000] FAT: invalid media value (0xb9)
[4297148.002000] VFS: Can't find a valid FAT filesystem on dev sda.
[4297148.012000] FAT: invalid media value (0xb9)
[4297148.012000] VFS: Can't find a valid FAT filesystem on dev sda.
[4297148.019000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4297148.024000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4297148.024000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4297148.024000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4297148.035000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4297148.035000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4297148.035000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4297148.135000] HFS+-fs: unable to find HFS+ superblock
[4297148.150000] HFS+-fs: unable to find HFS+ superblock
[4297148.214000] VFS: Can't find a HFS filesystem on dev sda.
[4297148.230000] VFS: Can't find a HFS filesystem on dev sda.
[4297148.240000] VFS: Can't find ext3 filesystem on dev sda.
[4297148.251000] VFS: Can't find ext3 filesystem on dev sda.
[4297148.334000] VFS: Can't find an ext2 filesystem on dev sda.
[4297148.344000] VFS: Can't find an ext2 filesystem on dev sda.
[4297148.486000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4297148.505000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4297148.644000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4297148.645000] SGI XFS Quota Management subsystem
[4297148.661000] XFS: bad magic number
[4297148.661000] XFS: SB validate failed
[4297148.674000] XFS: bad magic number
[4297148.674000] XFS: SB validate failed
[4297148.762000] JFS: nTxBlock = 2000, nTxLock = 16003

```

I know that the USB device works, I have no problems with mounting it in my Gentoo box....

Any ideas?

---

