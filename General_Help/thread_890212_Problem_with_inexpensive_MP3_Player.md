---
title: "Problem with inexpensive MP3 Player"
date: 2008-08-14
forum: General Help
---

### Post by altonbr on 2008-08-14
I purchased an inexpensive MP3 play by Coby. The model is MP-C582 and looks to be discontinued (hense why it was so inexpensive): [http://www.cobyusa.com/?p=prod&prod_num_id=1019&pcat_id=1001](http://www.cobyusa.com/?p=prod&prod_num_id=1019&pcat_id=1001).

A similar product is the MP-550: [http://cobyusa.com/?p=prod&prod_num_id=103&pcat_id=1001](http://cobyusa.com/?p=prod&prod_num_id=103&pcat_id=1001)

> 
    * Integrated flash memory
    * Plays MP3 and WMA digital music files
    * Random (shuffle) music playback
    * Key lock prevents accidental key presses
    * USB 2.0 Hi-Speed for fast file transfers
    * Integrated rechargeable battery

> 

    * Color: Black: 1G, 2G; Blue:1G; Red: 1G; Silver: 1G
    * Memory Capacity: 1GB, 2GB
    * Media Support: Integrated Flash
    * Format Support: Audio: MP3, WMA
    * Audio Output: 3.5mm Headphone
    * PC Interface: USB 2.0 Hi-Speed
    * Power: Integrated Rechargeable Lithium Polymer Battery
    * Battery Life: Audio Play Time: 5hr
    * Unit Dimension (WHD): 2.52" x 0.86" x 0.34"
    * Package Dimension (WHD): 5.5" x 8" x 1.75"
    * Carton (inner, master): 1, 10
    * UPC: 1G BLK: 7 16829 75503 7; 1G BLU: 7 16829 75513 6; 1G RED: 7 16829 75523 5; 1G SVR: 7 16829 75533 4; 2G BLK: 7 16829
    * Certifications: FCC, CE



What I am looking for the device to do is be recognized by Rhythmbox, but unfortunately, it is only recognized as a 1GB USB device.

When I select '1 GB Media' on the desktop, it appears have been mounted at /media/disk.

I've tried dragging and dropping the device into Rhythmbox, but to no avail.

Is there anything I can do so that Rhythmbox at least pretends it is an MP3 player?

I have the iPod and MTP plugins enabled and am using Ubuntu 8.04.1 & Rhythmbox 0.11.5

---

### Post by altonbr on 2008-08-14
Some more info:
```
$ dmesg | tail
[196174.802722] sd 7:0:0:0: [sdb] Write Protect is off
[196174.802729] sd 7:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[196174.802733] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[196174.805833] sd 7:0:0:0: [sdb] 2013696 512-byte hardware sectors (1031 MB)
[196174.806703] sd 7:0:0:0: [sdb] Write Protect is off
[196174.806709] sd 7:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[196174.806713] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[196174.806718]  sdb: sdb1
[196174.807922] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[196174.807981] sd 7:0:0:0: Attached scsi generic sg3 type 0

```

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0435fee7-8a0b-444e-b832-2cad6135ed91 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9e91a399-a8a9-4b5b-a3ed-ee5d33514939 /home           ext3    relatime        0       2
# /dev/sda6
UUID=2c850b2b-93ed-46f6-93f5-e15e95f7d5d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

```
$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2   *        1217        6658    43712865    7  HPFS/NTFS
/dev/sda3            6659       30394   190659420    5  Extended
/dev/sda5            6659       30269   189655326   83  Linux
/dev/sda6           30270       30394     1004031   82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031012352 bytes
8 heads, 32 sectors/track, 7866 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7866     1006832    b  W95 FAT32
```

---

### Post by mrtomservo on 2008-08-14
I had Coby MP3 players before, and they tend to be buggy.  Mine stopped reading from external sd cards within a month of purchase.  Sometimes it wouldn't show up at all when plugged into the USB.  You may have a hard time getting it to work right.  I'm assuming that it auto-mounts and sticks the 1gb or 2gb icon on your desktop?  If it does, then Rythmbox should find it - have you tried "Music - Search removable media"?

---

### Post by f37u5g0d on 2008-08-14
If it reckognizes it as 1gb media you can open it just like any folder and simply drag / drop your .mp3 files into it.  I do something very similar with my phone (although it uses a micro SD card) and my ipod (using rockbox).

---

### Post by altonbr on 2008-08-15
> **mrtomservo said:**
> I had Coby MP3 players before, and they tend to be buggy.  Mine stopped reading from external sd cards within a month of purchase.  Sometimes it wouldn't show up at all when plugged into the USB.  You may have a hard time getting it to work right.  I'm assuming that it auto-mounts and sticks the 1gb or 2gb icon on your desktop?  If it does, then Rythmbox should find it - have you tried "Music - Search removable media"?

Hmm, please don't tell me that :P Oh well, its cheap!

Yes, it automounts onto the desktop/Places menu.

I've tried "Search removable media" and it doesn't mount it in Rhythmbox... weird.

> **f37u5g0d said:**
> If it reckognizes it as 1gb media you can open it just like any folder and simply drag / drop your .mp3 files into it.  I do something very similar with my phone (although it uses a micro SD card) and my ipod (using rockbox).

Yeah, I can do that I guess, I just wonder why Rhythmbox won't detect it.

---

