---
title: "bizarre, taunting hard drive"
date: 2011-09-25
forum: Hardware
---

### Post by zindobora on 2011-09-25
Putting this under hardware because I think it might be a hardware problem...

My younger brother was downloading a video on his old hp tower (windows nt/2000) and I guess thought he needed to open up the computer and start unplugging things to look for a "driver" (computers aren't his thing). For months the thing wouldn't boot until one day I went in there and plugged in his hard drive for him.

I can't remember exactly what its original behavior was, but I remember it wouldn't boot the os. I tried installing windows 7, which eventually just gave me a cryptic "installation failed". I think I tried formatting the disk with cmd (on the windows 7 dvd) but it just sat at 0% all night. I think I did chkdsk too, it might have worked. whatever the case, it just comes to a blank screen (the _ cursor) after the hp screen.

Then I remembered a natty narwhal disk I had lying around! it did recognize that there was an existing windows nt/2000 os on the disk, but when I tried to install it gave me an "unable to create ext4 filesystem". I got to the terminal with ctrl-alt-f3 and tried cfdisk -l and just got a message about being unable to open /dev/sro1 as read-write(which I'm guessing is just the livecd). I think parted or maybe fdisk gave me a similar message. I have a fuzzy memory!

So it was working before he started unplugging things, which leaves me hope that maybe it's not a hard drive failure (and because ubuntu recognizes the windows nt os). But I'm actually not that good with computers! Any ideas as to what I should try next?

---

### Post by Blasphemist on 2011-09-25
Can you boot the live cd and use ubuntu? You know, connect to the internet, use firefox, see the desktop (is it unity by the way?). If all that works, you've basically tested the system short of the hard drive. From the live cd session, you can download and run the bootinfoscript. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That would let us see enough detail to give you a next step I think.

---

### Post by diasf on 2011-09-25
Indeed, start with a liveCD and work you way with it...
The fact it recognized as a 2k doesn't say much tbh. If I was you I would do the whole batch of system diagnostics, not only HD.

 And please say the pc was at least turned off before he started butchering it?

---

### Post by zindobora on 2011-09-26
Cool, I'll give it a shot! I don't have immediate access to the computer, so I'll have to wait until tomorrow, but I'll get back to you guys!

no unity btw, just gnome.

---

### Post by zindobora on 2011-09-26
(pretty sure he turned the pc off)

---

### Post by zindobora on 2011-10-15
Alright, it's been a couple weeks. Sorry I don't see my brother that often!

Ubuntu Live cd runs just fine. I used a crunchbang (little debian distro) live cd to run the boot info script since it comes ready with a driver for the wireless card.
---

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   388,757,503   388,755,456  83 Linux
/dev/sda2         388,759,550   390,721,535     1,961,986   5 Extended
/dev/sda5         388,759,552   390,721,535     1,961,984  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009230336 bytes
16 heads, 32 sectors/track, 15294 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,830,527     7,830,496   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        e935ff3a-6469-4228-ae95-c170eb0425b7   swap       
/dev/sdb1        FC0A-6403                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,shortname=winnt)
/dev/sr0         /live/image              iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  03 7f 00 05 00 18 01 7e  00 f3 00 03 00 06 00 0e  |.......~........|
00000010  36 96 00 00 03 7f 00 07  00 c4 01 a4 00 b3 00 03  |6...............|
00000020  00 08 26 37 02 68 00 00  03 7b 00 09 8a 02 8e 00  |..&7.h...{......|
00000030  f3 00 03 00 0a 04 c2 3f  03 18 00 00 00 03 fb 00  |.......?........|
00000040  0b 62 07 da 00 00 f3 00  03 00 0c 00 66 37 08 3c  |.b..........f7.<|
00000050  00 00 03 ff 00 0d 06 b4  08 a2 00 00 f3 00 03 00  |................|
00000060  0e 00 5c 6f 0f 56 00 01  00 00 f8 7f 0f b2 00 01  |..\o.V..........|
00000070  a4 00 01 05 6f 10 31 00  01 00 00 fa 02 07 10 36  |....o.1........6|
00000080  00 01 a4 00 03 2f 4f 10  3d 00 01 00 ea 04 05 6c  |...../O.=......l|
00000090  00 01 e4 00 05 00 0c 4f  10 71 00 01 00 ea 06 07  |.......O.q......|
000000a0  7d 00 01 e4 00 07 00 62  4f 10 84 00 01 00 fa 08  |}......bO.......|
000000b0  13 10 e6 00 01 a4 00 09  45 4f 10 f9 00 01 00 fe  |........EO......|
000000c0  0a 02 61 11 3e 00 01 a4  00 0b 31 4f 13 9f 00 01  |..a.>.....1O....|
000000d0  00 fe 0c 00 33 13 d0 00  01 e4 00 0d 03 5a 4f 14  |....3........ZO.|
000000e0  03 00 01 00 fa 0e 2e 17  5d 00 03 bc 04 03 00 02  |........].......|
000000f0  0c af 17 8b 00 03 01 05  fa 02 10 17 97 00 03 a8  |................|
00000100  06 02 0c 8e a7 00 03 07  eb 00 02 10 b3 00 03 38  |...............8|
00000110  08 00 02 8e c3 00 03 09  fe 00 00 fe 17 d3 00 03  |................|
00000120  e0 01 00 0a 4f 18 d1 00  03 04 fa 02 0e 18 db 00  |....O...........|
00000130  03 a0 03 5e 2f 18 e9 00  03 01 fa 04 0a 19 47 00  |...^/.........G.|
00000140  03 a0 05 18 0f 19 51 00  03 fa 06 0e 19 69 00 03  |......Q......i..|
00000150  a0 07 c4 0f 19 77 00 03  fa 08 26 1a 3b 00 03 a0  |.....w....&.;...|
00000160  09 8a 0f 1a 61 00 03 f6  0a 04 1a eb 00 03 a0 0b  |....a...........|
00000170  62 0f 1f ad 00 03 fe 0c  00 66 20 0f 00 03 60 0d  |b........f ...`.|
00000180  06 0f 20 75 00 03 fe 0e  00 5c 27 29 00 03 b8 0a  |.. u.....\')....|
00000190  00 02 0c 8f 27 85 00 03  0b fa 02 10 27 91 00 03  |....'.......'...|
000001a0  b8 0c 00 02 0c 8e a1 00  03 0e 63 00 02 ad 00 b8  |..........c.....|
000001b0  10 00 02 0e 8b 27 b9 03  13 fb 00 02 12 27 00 fe  |.....'.......'..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 
-------

sdb1 is just my thumb drive. anyone see anything revealing?

---

