---
title: "Can't mount hard drive.  -_-"
date: 2009-04-28
forum: Hardware
---

### Post by Phreakerr on 2009-04-28
Having a rather annoying problem.

My computer has two HDD's.,  one for the file system,  one for storing all my files,  so they are saved should i need to format my file system HDD.  Unfortunatly,  Ubuntu can't seem to mount my Storage drive.. can't think why..  (Also, i'm a linux n00b so i'm not really sure what "mounting" is...  all i know is i can't get to my files.)

Partitions are as follows:

HARD DRIVE 1, 160GB SATA:
"Filesystem" -- Ubuntu.  just got this HDD,  wanna copy all my files onto this,

HARD DRIVE 2, 40GB IDE:
"Storage" -- The mysterious unmountable partition.
"14.4 GB Media" -- Old Windows XP installation.. unneeded,  but it is mountable.

Pic attached.

Please help :(
Thanks in advance :)

[IMG]http://img218.imageshack.us/img218/3676/problem.png[/IMG]

---

### Post by x33a on 2009-04-28
post the output of 

```
sudo fdisk -l
cat /etc/fstab
```from the terminal.

---

### Post by Phreakerr on 2009-04-28
FDisk output:

[FONT=monospace]Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e1a9e1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3113    25005141    7  HPFS/NTFS
/dev/sda2            3114        4864    14064907+   f  W95 Ext'd (LBA)
/dev/sda5            3114        4864    14064876    c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19c219c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18748   150593278+  83  Linux
/dev/sdb2           18749       19457     5695042+   5  Extended
/dev/sdb5           18749       19457     5695011   82  Linux swap / Solaris
[/FONT]


Cat /etc/fstab output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9826a054-60c8-4f04-be88-b7834bbf1d35 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=09920acc-bdf6-4021-a945-0334e6fbf91a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Phreakerr on 2009-04-28
Also, just realised,  the "14.4 GB Media" is and old Ubuntu install,  not Windows.

---

### Post by x33a on 2009-04-28
is it the fat32 partition or the ntfs one?

for ntfs take a look here:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

for fat32 i have not idea.

---

### Post by Phreakerr on 2009-04-28
no idea :S  i'll try the NTFS one and post results,  cheers.

---

### Post by Phreakerr on 2009-04-28
Error Message:


Mounting /media/Storage failed.

Record 1 has no FILE magic (0x44414142)
Failed to open inode $MFTMirr: Input/output error
Failed to load $MFTMirr: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


Please remember these is no OS installed on "Storage",  it is just formatted space.

---

### Post by Phreakerr on 2009-04-28
just had an idea,  i could boot my Windows XP CD, use recovery console and run CHKDSK on the un-moutable drive,  see if it can find any errors and fix them

---

### Post by x33a on 2009-04-28
yes, you can try running chkdsk.

and if you don't have windows installed, then you should consider formatting the partitions to ext3.

also, take a look here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

really useful thread

---

### Post by Phreakerr on 2009-04-28
Argh,  CHKDSK had just told me that "The volume has one or more unrecoverable errors"

Either it wont fix it because theres not actual OS on it..  or it's corrupt :S

Ach well..  if it's corrupt, not much i can do about it really,  and this new SATA drive it on Ext3,  just needed to copy those files onto it..  picked a good time to pack in..  haha.

Thanks for the help though :)

---

