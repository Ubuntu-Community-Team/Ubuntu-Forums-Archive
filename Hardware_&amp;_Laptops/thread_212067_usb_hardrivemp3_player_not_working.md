---
title: "usb hardrive/mp3 player not working?"
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by Epica on 2006-07-09
[SIZE=2]hi i'm having trouble accessing a portable USB hardrive and mp3 player. [/SIZE][SIZE=2] the drive is a [/SIZE][SIZE=2]i-friend pes 2052 mp3 player that can be used as a portable hardrive. The unit has several card readers that can be accessed though windows which may explain that dmesg detected more than 1 drive.[/SIZE]
[SIZE=2]When i plug it in it appears in Nautilus file manager but when i click to access it an error message appears.[/SIZE]

> mount: wrong fs type, bad option, bad superblock on /dev/sdi1,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount 

[SIZE=2] I then went into terminal and the output of dmesg was this[/SIZE]
> [17182940.060000] usb 5-4: new high speed USB device using ehci_hcd and address 5
[17182940.192000] scsi4 : SCSI emulation for USB Mass Storage devices
[17182940.192000] usb-storage: device found at 5
[17182940.192000] usb-storage: waiting for device to settle before scanning
[17182945.192000]   Vendor:           Model: VP6210            Rev: 1.05
[17182945.192000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182945.192000] sd 4:0:0:0: Attached scsi removable disk sdf
[17182945.192000] sd 4:0:0:0: Attached scsi generic sg7 type 0
[17182945.196000]   Vendor:           Model: VP6210            Rev: 1.05
[17182945.196000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182945.196000] sd 4:0:0:1: Attached scsi removable disk sdg
[17182945.196000] sd 4:0:0:1: Attached scsi generic sg8 type 0
[17182945.200000]   Vendor:           Model: VP6210            Rev: 1.05
[17182945.200000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182945.200000] sd 4:0:0:2: Attached scsi removable disk sdh
[17182945.200000] sd 4:0:0:2: Attached scsi generic sg9 type 0
[17182945.224000]   Vendor:           Model: VP6210            Rev: 1.05
[17182945.224000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182945.224000] SCSI device sdi: 39070080 512-byte hdwr sectors (20004 MB)
[17182945.224000] sdi: assuming drive cache: write through
[17182945.224000] SCSI device sdi: 39070080 512-byte hdwr sectors (20004 MB)
[17182945.224000] sdi: assuming drive cache: write through
[17182945.224000]  sdi: sdi1
[17182945.940000] sd 4:0:0:3: Attached scsi disk sdi
[17182945.940000] sd 4:0:0:3: Attached scsi generic sg10 type 0
[17182945.944000] usb-storage: device scan complete
[17182946.340000] NTFS-fs warning (device sdi1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17182946.340000] NTFS-fs warning (device sdi1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17182946.340000] NTFS-fs error (device sdi1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182946.340000] NTFS-fs error (device sdi1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182946.340000] NTFS-fs error (device sdi1): ntfs_fill_super(): Not an NTFS volume.
[17182949.540000] NTFS-fs warning (device sdi1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17182949.744000] NTFS-fs warning (device sdi1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17182949.748000] NTFS-fs error (device sdi1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182949.748000] NTFS-fs error (device sdi1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182949.748000] NTFS-fs error (device sdi1): ntfs_fill_super(): Not an NTFS volume.
 
 [SIZE=3][SIZE=2] I think Ubuntu might be trying to mount the drives as NTFS. The drive is formatted as fat32 and can easily be accessed by windows. Does anyone know how i could get ubuntu to mount this drive as fat32 or get it to recognise and auto mount fat32 drives and partitions?

any help greatly appreciated[/SIZE] 

[/SIZE]

---

### Post by kb3hkg on 2006-07-10
if it made it that far then I'd say check /etc/fstab if there are entries in there try switching them to fat32 from ntfs and see if that helps.

---

### Post by Epica on 2006-07-10
had a look at the fstab file, but there was no entry for the device.
Tried to mount the drive via the command line

> mount -t vfat /dev/sdi /mnt/sdi

but looking at syslog again after typing that command it said it couldn't find a valid fat filesystem on /dev/sdi. I think the filesystem may be corrupt although it works on windows fine.

---

### Post by kb3hkg on 2006-07-11
try using a partitioning utility: fdisk cfdisk or grparted. Find out what exactly is on there in the way of filesystems.

---

