---
title: "lost partition"
date: 2008-06-15
forum: Hardware
---

### Post by cyreald on 2008-06-15
hello
I have an external harddrive that I have partitionned in two parts (sdb)
i used it for amarok and it never mounted the two parts to the same destinations and got my softs panicked so i wanted to manually assign my partitions mount points
I messed up
now one is not working
also i changed format
i don't remember what i did, but for months now sdb1 mounts fine and sdb2 doesn't
here are the messages I get
please help I'd like to get my othe partition back

arwan@marwan-laptop:~$ sudo fdisk -l
[sudo] password for marwan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9606        9729      996030   82  Linux swap / Solaris
/dev/sda2               1        1095     8795556   83  Linux
/dev/sda3   *        1096        9605    68356575   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x208c8ae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       35305   283587381    c  W95 FAT32 (LBA)
/dev/sdb2           35306       60801   204796620    7  HPFS/NTFS


marwan@marwan-laptop:~$ sudo mount -a
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
marwan@marwan-laptop:~$

---

### Post by kevmitch on 2008-06-15
> **cyreald said:**
> 
also i changed format


That sends shivers down my spine. If this really did involve reformatting one of the partitions, the data is likely gone unless you somehow copied it off before the reformat and copied it back afterwords.

> **cyreald said:**
> 
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Do you have windows installed? If so do what it says and run a chkdsk from within windows. Since it isn't a system drive, you'll likely be able to do this with out rebooting. I can't remember exactly where, something like "System Management Utilties". You should probably be able to get there  by right clicking mycomputer. Maybe someone with windows in more recent memory can help out here.

---

### Post by Virus_Muncher on 2008-06-16
> **cyreald said:**
> hello
I have an external harddrive that I have partitionned in two parts (sdb)
i used it for amarok and it never mounted the two parts to the same destinations and got my softs panicked so i wanted to manually assign my partitions mount points
I messed up
now one is not working
also i changed format
i don't remember what i did, but for months now sdb1 mounts fine and sdb2 doesn't
here are the messages I get
please help I'd like to get my othe partition back

arwan@marwan-laptop:~$ sudo fdisk -l
[sudo] password for marwan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9606        9729      996030   82  Linux swap / Solaris
/dev/sda2               1        1095     8795556   83  Linux
/dev/sda3   *        1096        9605    68356575   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x208c8ae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       35305   283587381    c  W95 FAT32 (LBA)
/dev/sdb2           35306       60801   204796620    7  HPFS/NTFS


marwan@marwan-laptop:~$ sudo mount -a
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
marwan@marwan-laptop:~$
probably you corrupted your partition table .. 

i had a similar problem .. i had ubuntu and windows xp installed on my laptop ... i dunno what happened but i just lost the link to my xp and whenever i tried selecting XP from the GRUB list, it always used to say "Disk Error, Press any key to Restart" 

I tried many things to get back my XP but it was just useless ... i found a software called testdisk .. i think you could 

> sudo apt-get install testdisk

it is a nice and clean software to repair your partition tables, boot sector etc ...

this one fixed everything on my laptop

cheers

---

