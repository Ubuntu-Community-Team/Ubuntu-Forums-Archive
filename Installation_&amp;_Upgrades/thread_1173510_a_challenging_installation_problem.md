---
title: "a challenging installation problem"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by harrisoftware on 2009-05-29
I have a machine that was a windows server.
it has 2 additional sata cards in it for a total of 10 drives available including the IDE (4 channel) and SATA (2 channel) on the MB (Asus A8S-X).
 
I unplugged ALL the SATA drives so I could install ubuntu-server on the first IDE.
great.
plugged all the SATA drives back in, set the bios to boot from the 1st IDE (which shows up second last now in the drive list.
great.
it works.
eventually managed to get all the SATAs mounted.
great.
I can see all my windows files that I might need some day (whatever).
so I install ubuntu-desktop to the 2nd IDE drive (all drives attached)
it reboots.
there's no entry in GRUB for the new ubuntu desktop on 2nd IDE
 
i've tried a bunch of things, but my Linux is a bit rusty (not much reliance on tools like Webmin I guess!)
 
How can I get this to boot to ubuntu-desktop???
or should i just unplug all the satas again and reinstall ubuntu desktop??
 
Warren
 
-------
 
here's the drivelist reported from the ubuntu-server (when booted)
Disk name    Total size    Make and model    Partitions       
SCSI device A 465.76 GB ATA Hitachi HDP72505 1 
SCSI device B 465.76 GB ATA Hitachi HDP72505 1 
SCSI device C 149.05 GB ATA Maxtor 6V160E0  1 
SCSI device D 233.76 GB ATA Maxtor 7Y250M0  1 
SCSI device E 149.05 GB ATA ST3160812AS  1 
SCSI device F 76.69 GB ATA HDS728080PLAT20  3 
SCSI device G 76.69 GB ATA HDS728080PLAT20  3 
 
here's my grub (oh, I also tried to get it to Boot Windows - ya right!)
 
title 		Ubuntu 9.04 Server
uuid 		b26a9bae-a570-4eca-b5d1-a997d55295a1
kernel 		/boot/vmlinuz-2.6.28-11-server root=UUID=b26a9bae-a570-4eca-b5d1-a997d55295a1 ro quiet splash 
initrd 		/boot/initrd.img-2.6.28-11-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid		b26a9bae-a570-4eca-b5d1-a997d55295a1
kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=b26a9bae-a570-4eca-b5d1-a997d55295a1 ro  single
initrd		/boot/initrd.img-2.6.28-11-server

title		Ubuntu 9.04, memtest86+
uuid		b26a9bae-a570-4eca-b5d1-a997d55295a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# this entry added for non-linux OS
# on /dev/sdd1

title Windows XP x64
root (hd3,0)
makeactive
chainloader +1

title Ubuntu 9.04 Desktop
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=49a41af4-2a61-43c5-a7fe-2a132ab7c256 ro splash
initrd /boot/initrd.img-2.6.28-11-generic

here's the fdisk output:
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x245567b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x245567b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cbbb023

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2470718f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   42  SFS

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae0aae0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdf: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e60de20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        9598    77095903+  83  Linux
/dev/sdf2            9599       10011     3317422+   5  Extended
/dev/sdf5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/sdg: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec1f9c40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        9598    77095903+  83  Linux
/dev/sdg2            9599       10011     3317422+   5  Extended
/dev/sdg5            9599       10011     3317391   82  Linux swap / Solaris

block IDs:
 
/dev/sda1: UUID="C448C51048C501E2" LABEL="MIRROR500" TYPE="ntfs" 
/dev/sdb1: UUID="C448C51048C501E2" LABEL="MIRROR500" TYPE="ntfs" 
/dev/sdc1: UUID="02D827BED827AEBB" LABEL="MAXTOR160" TYPE="ntfs" 
/dev/sdd1: UUID="76D426D9D4269AFF" LABEL="FILESERVER" TYPE="ntfs" 
/dev/sde1: UUID="38D092A1D0926542" LABEL="XPx64" TYPE="ntfs" 
/dev/sdf1: UUID="b26a9bae-a570-4eca-b5d1-a997d55295a1" TYPE="ext3" 
/dev/sdf5: TYPE="swap" UUID="d357ea73-0326-44c2-a526-f65bdfdd18b0" 
/dev/sdg1: UUID="49a41af4-2a61-43c5-a7fe-2a132ab7c256" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdg5: TYPE="swap" UUID="b77021ea-fac8-43cb-8006-72425d24bd99

---

### Post by harrisoftware on 2009-05-30
bump
 
I'd just like to know if I can actually get this to boot these other OSes or should i just yank all the drives but the 2 ide and reinstall ubuntu desktop
 
why does ubuntu not see the drives as reordered in the bios?? btw

---

### Post by lindsay7 on 2009-05-30
I do not know what all is going on here, but I think that the lines after your windows boot info need to be above the line


### END DEBIAN AUTOMAGIC KERNELS LIST



> title Ubuntu 9.04 Desktop
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=49a41af4-2a61-43c5-a7fe-2a132ab7c256 ro splash
initrd /boot/initrd.img-2.6.28-11-generic

---

### Post by harrisoftware on 2009-06-01
the lines between the 
###start and 
### END DEBIAN AUTOMAGIC KERNELS LIST### 
are managed by webmin and if you put stuff in there, you might lose it.
 
its not that the entries don't show up in the list, its that when you choose them, it bombs out trying to boot - can't find OS, bad partition selected etc...
 
I'm thinking its something a noob like me just can't figure out on his own but an expert could spot right away.

---

