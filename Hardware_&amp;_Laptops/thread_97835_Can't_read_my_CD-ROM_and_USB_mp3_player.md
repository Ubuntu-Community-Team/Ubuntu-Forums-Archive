---
title: "Can't read my CD-ROM and USB mp3 player"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by wagdog on 2005-12-01
FYI, I'm on Breezy.  Both show under Places/Computer but when I try to open them I get the errors below.  The CD-ROM worked fine before a recent set of updates (not sure which ones) and I'm not sure about the mp3 player (it worked fine on 5.04).  Please help!  

===================================================
USB MP3 player error=

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

====================================================
CD-ROM error = 

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by wagdog on 2005-12-02
More info - 

When I try to mount my USB thumb drive (which worked perfect in 5.04) I get the same errors as above.  When I enter dmesg I get the following:

[4303729.654000] Initializing USB Mass Storage driver...
[4303729.661000] scsi0 : SCSI emulation for USB Mass Storage devices
[4303729.670000] usb-storage: device found at 2
[4303729.670000] usb-storage: waiting for device to settle before scanning
[4303729.670000] usbcore: registered new driver usb-storage
[4303729.670000] USB Mass Storage support registered.
[4303734.674000]   Vendor: KINGSTON  Model: USB DRIVE         Rev: 1.12
[4303734.674000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
[4303734.695000] usb-storage: device scan complete
[4303734.909000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
[4303734.914000] sda: Write Protect is off
[4303734.914000] sda: Mode Sense: 23 00 00 00
[4303734.914000] sda: assuming drive cache: write through
[4303734.930000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
[4303734.935000] sda: Write Protect is off
[4303734.935000] sda: Mode Sense: 23 00 00 00
[4303734.935000] sda: assuming drive cache: write through
[4303734.935000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4303734.948000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4303745.391000] UDF-fs: No VRS found
[4303745.461000] UDF-fs: No VRS found
[4303745.908000] Unable to identify CD-ROM format.
[4303746.250000] Unable to identify CD-ROM format.
[4303746.327000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensiti ve!
[4303746.330000] FAT: invalid media value (0x00)
[4303746.330000] VFS: Can't find a valid FAT filesystem on dev sda.
[4303746.343000] FAT: invalid media value (0x00)
[4303746.343000] VFS: Can't find a valid FAT filesystem on dev sda.
[4303746.379000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4303746.392000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use opti on nls=<charsetname> in the future.
[4303746.395000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4303746.395000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Abo rting without trying to recover.
[4303746.395000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4303746.441000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4303746.441000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Abo rting without trying to recover.
[4303746.441000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4303746.498000] HFS+-fs: unable to find HFS+ superblock
[4303746.513000] HFS+-fs: unable to find HFS+ superblock
[4303746.564000] VFS: Can't find a HFS filesystem on dev sda.
[4303746.580000] VFS: Can't find a HFS filesystem on dev sda.
[4303746.592000] VFS: Can't find ext3 filesystem on dev sda.
[4303746.605000] VFS: Can't find ext3 filesystem on dev sda.
[4303746.619000] VFS: Can't find an ext2 filesystem on dev sda.
[4303746.632000] VFS: Can't find an ext2 filesystem on dev sda.
[4303746.712000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4303746.736000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4303746.816000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4303746.817000] SGI XFS Quota Management subsystem
[4303746.851000] XFS: bad magic number
[4303746.851000] XFS: SB validate failed
[4303746.867000] XFS: bad magic number
[4303746.867000] XFS: SB validate failed
[4303746.918000] JFS: nTxBlock = 1998, nTxLock = 15986


I can't be the only person with this problem can I?

---

### Post by wagdog on 2005-12-04
I tried going back to the previous kernel (2.6.12-9-386) to see if that helped.  It did not.  The funny thing is if I boot from the Live CD everything works just fine so an update somewhere along the line broke things.  Is there anyway to figure out what has benn added or updated since an install?

---

### Post by wagdog on 2005-12-06
I have finally solved my problem after spending hours reading any post that looked like it might pertain and trying any and all solutions.  What it turned out to be is the user 'hal' did not have permissions to use these devices.  Once I gave hal these permissions everything worked like it used to.  This change must have happened during one of the updates as my devices used to work and then suddenly stopped.  Fine, mistakes happen, but it should not have been this hard to get it resolved.

Rant #1: Why didn't the error messages I received mention this fact?  Some process somewhere must have known it was a permission issue.  Would it be so hard to have this information purcolate to the end user?  Something like "User hal does not have permission to access the requested device." would have been nice.  If other OS's can do it why not Ubuntu?

Rant #2: With so many people apparently having the same problem, why isn't there a stickly with the title "If you are having problems with your CD-ROM and USB devices read this" and then list the possible solutions?  I see a lot of people all scrambling looking for a fix for their (apparently common) dilemma.

---

