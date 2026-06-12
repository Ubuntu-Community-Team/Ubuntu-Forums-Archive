---
title: "segate barracuda ATA IV deson't getting mounted"
date: 2012-10-07
forum: Hardware
---

### Post by ARDV on 2012-10-07
hello
i have
segate barracuda ATA IV, model: ST340016A (40 gb)
it doesn't getting mounted by ubuntu

it says:
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdg,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

when writing dmesg | tail in the shell, it shows:
[  712.695115] sd 13:0:0:0: [sdg] Assuming drive cache: write through
[  712.697599] sd 13:0:0:0: [sdg] No Caching mode page present
[  712.697603] sd 13:0:0:0: [sdg] Assuming drive cache: write through
[  712.708908]  sdg:
[  712.711470] sd 13:0:0:0: [sdg] No Caching mode page present
[  712.711474] sd 13:0:0:0: [sdg] Assuming drive cache: write through
[  712.711478] sd 13:0:0:0: [sdg] Attached SCSI disk
[  742.884716] usb 2-1.6.4: reset high-speed USB device number 11 using ehci_hcd
[  743.128309] ufs was compiled with read-only support, can't be mounted as read-write
[  757.377108] ufs was compiled with read-only support, can't be mounted as read-write


in the system utility it says: file system driver not installed
do i have to install any drivers or some

and is there any way to repair it if it's damaged?


HELP PLEASE

---

### Post by Bashing-om on 2012-10-07
ARDV; Hi !

Some additional info to be helpful:
what version are you using ? (so we can advise on paths)
How are you attaching the drive ?

with the drive installed please post the output of terminal command:
```
sudo fdisk -lu
``` <lower case "L">

Will show us what we have to work with for starters.
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by ARDV on 2012-10-08
> **Bashing-om said:**
> ARDV; Hi !

Some additional info to be helpful:
what version are you using ? (so we can advise on paths)
How are you attaching the drive ?

with the drive installed please post the output of terminal command:
```
sudo fdisk -lu
``` <lower case "L">

Will show us what we have to work with for starters.
[INDENT]regards <==BDQ

[/INDENT]

i'm using the version 12.04

fdisk -lu
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   215867391   107830272    7  HPFS/NTFS/exFAT
/dev/sda3       215867392   850745343   317438976    7  HPFS/NTFS/exFAT
/dev/sda4       850745344  1465145343   307200000    7  HPFS/NTFS/exFAT

Disk /dev/sdg: 40.0 GB, 40020664320 bytes
64 heads, 32 sectors/track, 38166 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73d46187

   Device Boot      Start         End      Blocks   Id  System

```

i have another question, why i my update manager doesn't show the 12.10 version?? 
i've choosed: notify me of a new ubuntu version: for any new version, i understand that it have to show the beta version in update!, so how can i upgrade to the latest beta version?

---

