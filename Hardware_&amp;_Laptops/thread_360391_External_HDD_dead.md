---
title: "External HDD dead?"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by daller on 2007-02-13
Hi there,

I'm trying to restore data from an external HDD for one of my friends!

Dmesg:

```

[  928.502356] usb 4-5: new high speed USB device using ehci_hcd and address 12
[  928.635899] usb 4-5: configuration #1 chosen from 1 choice
[  928.636577] scsi1 : SCSI emulation for USB Mass Storage devices
[  928.636639] usb-storage: device found at 12
[  928.636641] usb-storage: waiting for device to settle before scanning
[  933.626375] usb-storage: device scan complete
[  933.627126] scsi 1:0:0:0: Direct-Access     ST312002 D56E                  PQ: 0 ANSI: 2 CCS
[  933.629094] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  933.629842] sda: Write Protect is off
[  933.629846] sda: Mode Sense: 00 38 00 00
[  933.629848] sda: assuming drive cache: write through
[  933.630836] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  933.631586] sda: Write Protect is off
[  933.631590] sda: Mode Sense: 00 38 00 00
[  933.631592] sda: assuming drive cache: write through
[  933.631595]  sda: sda1
[  933.649389] sd 1:0:0:0: Attached scsi disk sda
[  933.649438] sd 1:0:0:0: Attached scsi generic sg0 type 0

```

Running "cfdisk /dev/sda" tells me that it's an NTFS filesystem!

I go to "/etc/fstab" and add the device:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9c685961-fd40-43b8-9de6-6be62338b237 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d4b685b9-14d0-42dd-b6a2-9920ea9d68bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1     ntfs    defaults        0       0

```

Trying to mount the drive (creating /media/sda1, and running "sudo mount /media/sda1") gives me this in the terminal:

```

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

...and this is dmesg:

```

[ 1133.587333] NTFS-fs error (device sda1): map_mft_record_page(): Mft record 0x0 is corrupt.  Run chkdsk.
[ 1133.587342] NTFS-fs error (device sda1): map_mft_record(): Failed with error code 5.
[ 1133.587347] NTFS-fs error (device sda1): ntfs_read_locked_inode(): Failed with error code -5.  Marking corrupt inode 0x0 as bad.  Run chkdsk.
[ 1133.587352] NTFS-fs error (device sda1): ntfs_read_inode_mount(): ntfs_read_inode() of $MFT failed. BUG or corrupt $MFT. Run chkdsk and if no errors are found, please report you saw this message to linux-ntfs-dev@lists.sourceforge.net
[ 1133.587358] NTFS-fs error (device sda1): ntfs_fill_super(): Failed to load essential metadata.

```

Edit: I don't have the chkdsk tool! - Where do I get it, and will it help at all?

What can I do to fix this?

---

### Post by markitect on 2007-02-28
looks like a file system error install the package ntfsprogs
pop open a terminal and run
```

sudo apt-get install ntfsprogs
ntfsresize -fi /dev/sda1

```
an ntfs checkdisk hasnt been made yet(that i know of), but the resize program does some checking and recovery that might do the trick

---

