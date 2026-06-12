---
title: "USB thumb drive automounting"
date: 2008-08-02
forum: General Help
---

### Post by Apkerr on 2008-08-02
Hardy Heron 8.04

I can't get my USB thumb drive to automount.

When I plug in the drive and type 'dmesg' I get:

[ 2208.171367] usb 5-5: new high speed USB device using ehci_hcd and address 16
[ 2208.304264] usb 5-5: configuration #1 chosen from 1 choice
[ 2208.305077] scsi12 : SCSI emulation for USB Mass Storage devices
[ 2208.305628] usb-storage: device found at 16
[ 2208.305633] usb-storage: waiting for device to settle before scanning
[ 2213.294594] usb-storage: device scan complete
[ 2213.295321] scsi 12:0:0:0: Direct-Access              Staples Relay    0.1  PQ: 0 ANSI: 2
[ 2213.297422] sd 12:0:0:0: [sdd] 2001888 512-byte hardware sectors (1025 MB)
[ 2213.298032] sd 12:0:0:0: [sdd] Write Protect is off
[ 2213.298042] sd 12:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 2213.298048] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[ 2213.300885] sd 12:0:0:0: [sdd] 2001888 512-byte hardware sectors (1025 MB)
[ 2213.301510] sd 12:0:0:0: [sdd] Write Protect is off
[ 2213.301517] sd 12:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 2213.301521] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[ 2213.301528]  sdd: sdd1
[ 2213.302613] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[ 2213.302679] sd 12:0:0:0: Attached scsi generic sg4 type 0


The drive appears in my Places->Computer as "USB Drive" but I get an error "Unable to mount location; Can't mount file" when I try to open it.
GParted shows the drive located at sdd1.
Typing "gnome-mount -d /dev/sdd1" mounts the drive, but it would be nice if it would automount like it does in XP.

I've searched through the forums and have found several posts with the same problems but no solutions so far. Any suggestions?

---

### Post by rEbyTer on 2008-08-02
Please copy paste what is inside **/etc/fstab** file.

---

### Post by Apkerr on 2008-08-02
Here's the fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4206661d-f4b3-4ecc-85ee-a6333431e6be /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ee18e414-c02f-4a26-a190-d5fabc0b39e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# /dev/sdb1
UUID=368829A788296719
/dev/sdb1  /media/Storage1-System  ntfs  suid,dev,exec  0  0
/dev/sdc1  /media/Windows-main  ntfs  user,suid,dev,exec  0  0

/dev/sdd1  /media/external  auto users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
 

I added the last line after searching multiple posts on this topic. Other than allowing me to do a "mount /dev/sdd1" command in terminal, it doesn't seem to do anything.

---

### Post by Apkerr on 2008-08-02
I may have been a bit unclear. The drive does "automount" in the sense that it mounts on boot as long as it's in the USB port at the time (because of the line in fstab). 

What it won't do is mount when I plug it in and the computer's already running.

---

### Post by rEbyTer on 2008-08-03
What filesystem are you using on USB thumb drive ?
Also paste the output of:
```
$ sudo fdisk -l
```

---

### Post by Apkerr on 2008-08-03
The thumb drive is formatted as FAT32.

sudo fdisk -l: (thumb drive inserted but not mounted)

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27152714

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11688    93883828+  83  Linux
/dev/sda2           11689       12188     4016250    5  Extended
/dev/sda5           11689       12188     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a172a16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29d329d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30019   241126168+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2           30019       30401     3069832+   7  HPFS/NTFS

Disk /dev/sdd: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x0000f288

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         992      999813+   b  W95 FAT32

---

### Post by rEbyTer on 2008-08-03
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=deae8853-9fb0-4308-b867-3c000f1e5eb4 /               ext2    relatime,errors=remount-ro 0       1
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

This is my fstab :) .... and my external HDD does automount when I turn it on and is bombarding me with Thunar(like nautilus) windows :). I have 2 partitions and I really don't like to shut down two windows everytime my HDD is going on:|

Please try to remove that sdd line :| in your fstab. When it says that you cannot mount that drive you may have invalid fstab line, so be careful.

---

### Post by Apkerr on 2008-08-03
The sdd1 line wasn't in my fstab file until I put it there. 

In order to mount the drive without that line I have to issue a "sudo mount" command with all the options, etc. It will not automatically mount.

With that line in there I can mount it with just a "mount" command. It will also mount on boot if the drive is connected.

What I want to do is have it automatically mount when I hotplug it, the way it does in XP. It doesn't seem to matter if that line is in the fstab file or not, it doesn't hotplug either way.

---

### Post by rEbyTer on 2008-08-03
Very strange. :|

You may look here.Try to hack udev.
[http://ubuntuforums.org/showpost.php?p=1537617&postcount=6](http://ubuntuforums.org/showpost.php?p=1537617&postcount=6)

---

### Post by echo6 on 2008-08-10
Remove the entry from /etc/fstab!  hal honours entries it sees in /etc/fstab thus it won't autmount them as the system takes preference according to the mount options.  Actually it is gnome-mount that is responsible for mounting.  After you have removed the entry from /etc/fstab make sure that you have automount enabled using gconf-editor,  navigate to /apps/nautilus/preferences, ensure there is a tick in the box for media_automount.  You may also want to check under /apps/volume-manager, although autmount_media is not selected on my system and automount works fine.

---

### Post by Apkerr on 2008-08-12
That didn't make a difference. I took out the entry and automount was already enabled in both /apps/nautilus/preferences and apps/volume-manager.

It's not a big deal to mount it manually, it's just annoying.

---

