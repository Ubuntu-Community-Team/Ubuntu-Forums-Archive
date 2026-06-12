---
title: "mount issues"
date: 2012-07-03
forum: Hardware
---

### Post by Tijn1978 on 2012-07-03
Hi out there,

My issue is that I can' t boot into my desktop after changing the /etc/fstab file.
I can however use a live-cd to boot and then navigate to folders using the shell.
My current fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# / was on /dev/sda1 during installation
UUID=33621e7d-d8d3-46a0-9037-7f903b580dfe /     errors=remount-ro   ext4    0 1
#errors=remount-ro        1


# swap was on /dev/sda5 during installation
UUID=77b6c795-62dd-4dc4-abb7-19a73c3f1e4f none            swap    sw              0       0

#UUID=356e1882-ffe0-4f09-b453-1de985a747a0 /                    ext4    errors=remount-ro       0   $

#/dev/sdc1 /media/d2 / ext4 errors=remount-ro 0 1
#UUID=f363885b-e7a1-42bb-8d2e-42abd90dc6db /                    ext4    errors-remount-ro 0     1

#/dev/sdb1 /media/data ext4   rw none  0 0
#/dev/sdc1 /media/data2 ext4  rw none  0 0

Here's som extra info:
sudo os-prober:
/dev/sda1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

sudo fdisk-l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bcc69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   226054143   113026048   83  Linux
/dev/sda2       226056190   234440703     4192257    5  Extended
/dev/sda5       226056192   234440703     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cbb55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ec396

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1945137151   972567552   83  Linux
/dev/sdc2      1945139198  1953523711     4192257    5  Extended
/dev/sdc5      1945139200  1953523711     4192256   82  Linux swap / Solaris

This is with live-cd:
  sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="33621e7d-d8d3-46a0-9037-7f903b580dfe" TYPE="ext4" 
/dev/sda5: UUID="77b6c795-62dd-4dc4-abb7-19a73c3f1e4f" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660" 
/dev/sdb1: LABEL="data" UUID="356e1882-ffe0-4f09-b453-1de985a747a0" TYPE="ext4" 
/dev/sdc1: LABEL="data2" UUID="f363885b-e7a1-42bb-8d2e-42abd90dc6db" TYPE="ext4" 
/dev/sdc5: UUID="d32cfb81-88b2-41d4-88f2-44c9d9946d23" TYPE="swap" 

Please tell what do I put in my fstab to make it run again.
If I boot now, it'll stop with errors and I have a shell with read-only permission.

Please help,
Martijn

---

### Post by Tijn1978 on 2012-07-03
New fstab file won' t run either:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# / was on /dev/sda1 during installation
UUID=33621e7d-d8d3-46a0-9037-7f903b580dfe /     errors=remount-ro   ext4    0 1

# swap was on /dev/sda5 during installation
UUID=77b6c795-62dd-4dc4-abb7-19a73c3f1e4f none            swap    sw              0       0


#sdb?
UUID=f363885b-e7a1-42bb-8d2e-42abd90dc6db /media/data2 none ext4  0 1
UUID=d32cfb81-88b2-41d4-88f2-44c9d9946d23 none  swap sw 0 0

#sdc?
UUID=356e1882-ffe0-4f09-b453-1de985a747a0 /media/data none ext4 0 1

Greetz,
Martijn

---

### Post by ahallubuntu on 2012-07-03
Comment out any line in your fstab you aren't sure about by putting a "#" character at the beginning of each line.

The only lines you REALLY need are these - comment out the rest of them with the "#" character in front for now.

proc /proc proc nodev,noexec,nosuid 0 0
UUID=33621e7d-d8d3-46a0-9037-7f903b580dfe / errors=remount-ro ext4 0 1
UUID=77b6c795-62dd-4dc4-abb7-19a73c3f1e4f none swap sw 0 0

If you changed the UUID (blkid) of any partition, you'd need to change the UUID in your /etc/fstab file .  But it sounds unlikely that you did that.

Try to avoid any mount points with /media in your fstab file - leave those for Nautilus - use /mnt instead for devices you wish to mount in your fstab.  Don't put any external (USB) device in your fstab file unless you will ALWAYS have it plugged in and turned on, otherwise you won't be able to boot.

---

### Post by Tijn1978 on 2012-07-04
Did as you asked and it still won' t boot.
current fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# / was on /dev/sda1 during installation
UUID=33621e7d-d8d3-46a0-9037-7f903b580dfe /     errors=remount-ro   ext4    0 1

# swap was on /dev/sda5 during installation
UUID=77b6c795-62dd-4dc4-abb7-19a73c3f1e4f none            swap    sw              0       0


#sdb?
#UUID=f363885b-e7a1-42bb-8d2e-42abd90dc6db /media/data none ext4  0 1
#UUID=d32cfb81-88b2-41d4-88f2-44c9d9946d23 none  swap sw 0 0

#sdc?
#UUID=356e1882-ffe0-4f09-b453-1de985a747a0 /media/data2 none ext4 0 1
---------------------------------------------------------------------------------------------------------------------
dmesg output from last boot in /var/log/dmesg:
[    1.377455] scsi 0:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
[    1.377580] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.377604] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.377639] sd 0:0:0:0: [sda] Write Protect is off
[    1.377642] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.377663] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.378379]  sda: sda1 sda2 < sda5 >
[    1.378639] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH16A6S   YA16 PQ: 0 ANSI: 5
[    1.378732] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.381467] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.381472] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.381616] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.381674] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.381801] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    1.381901] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.381921] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.381942] sd 2:0:0:0: [sdb] Write Protect is off
[    1.381945] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.382004] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.382069] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EAVS-00D 01.0 PQ: 0 ANSI: 5
[    1.382169] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.382212] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.382220] sd 3:0:0:0: [sdc] Write Protect is off
[    1.382223] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.382249] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.403067]  sdb: sdb1
[    1.403301] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.422775]  sdc: sdc1 sdc2 < sdc5 >
[    1.423142] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.423220] Freeing unused kernel memory: 740k freed
[    1.423554] Write protecting the kernel text: 5816k
------------------------------------------------------------------------------------------------------------------------------


Is there maybe a tool that can regenerate my fstab, a rescue disk that I can burn or USB stick? This is really annoying. Are there any other things that I can do? Maybe some more error logs I can post?
Thanks for the reply and help so far.


Groet,
Martijn


ps) It might help if I had that read-only removed. Now I have to boot in live-cd in order to change. If gain shell access with a ' normal'  boot I am not able to change anything because it is read-only.

---

### Post by Tijn1978 on 2012-07-04
I have now commented everything and now it boots again.
I really need a GUI (preferably) to set it up again.
Please, just a tool to setup fstab and the other files that are read during boot.

Thanks in advance.

Greeetz,
Martijn

---

### Post by Tijn1978 on 2012-07-05
sudo apt-get install pysdm
This tool rewrites your fstab.


Thanks for whoever helped or tried to help.

---

