---
title: "[SOLVED] External HDD suddenly fails to mount"
date: 2008-06-14
forum: Hardware
---

### Post by goathunter on 2008-06-14
Hello. Im using ubuntu 8.04 on an Acer aspire 3000 laptop. I have been using an external hard drive for a couple of years and no probs. Today using as nrmal and suddenly can't open file on it. Turn it off and on and I get the error message in the screenshot. Tried it with a 7.10 live cd and got the same error. Output of dmesg | tail is

> marcus@marcus-laptop:~$  dmesg | tail
[  769.804763] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  769.804766] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  769.806002] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  769.807006] sd 2:0:0:0: [sdb] Write Protect is off
[  769.807014] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  769.807017] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  769.807024]  sdb: sdb1
[  769.823706] sd 2:0:0:0: [sdb] Attached SCSI disk
[  769.823750] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  867.135786] EXT3-fs: journal inode is deleted.
marcus@marcus-laptop:~$ 


Any help would be appreciated as most of my files are on this drive.
Thankyou for your time


Edit  After reading other posts by people with a similar problem tried this
> The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

marcus@marcus-laptop:~$  /dev/sd1
bash: /dev/sd1: No such file or directory
marcus@marcus-laptop:~$  e2fsck -b 8193 /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 


Should I continue? I don't really understand how e2fscuk works and am not keen to wipe my entire drive.

contents of etc/fstab are 
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6c1b8ed8-ca98-4a89-bc70-e438bacb5898 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fe52cd99-8ab6-4854-8114-9898f4d610ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by goathunter on 2008-06-15
Problem solved. Opened up gpartd from a 7.10 live cd. Opened up the drive in that (/dev/sdb1/) Clicked check and repair. Took about 14 minutes. Drive still failed to detect in the live cd so I rebooted and took it out. After booting 8.04 from my harddrive, the external drive was being detected again no worries.

---

