---
title: "Strange problem with DVDROM and DMA"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by dhyams on 2005-12-21
I have a system that I just switched over from Fedora Core 3 to Ubuntu 5.10 (breezy).  I watched DVD's with no problem under FC3 (and still can, if I boot FC3).  But, under Ubuntu, DVD playback is very, very jerky.

So, the obvious thing to do was to enable DMA.  Nothing doing; if I enable DMA for the DVDROM drive, I get all kinds of read errors in my system log, and the DVD does not play at all.  Stuff like this in /var/log/messages:

[FONT="Courier New"]ec 21 18:56:49 localhost kernel: [4295358.486000] hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Dec 21 18:56:49 localhost kernel: [4295358.486000] hdd: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Dec 21 18:56:49 localhost kernel: [4295358.486000] ide: failed opcode was: unknown
Dec 21 18:56:49 localhost kernel: [4295358.486000] end_request: I/O error, dev hdd, sector 64
Dec 21 18:56:49 localhost kernel: [4295358.487000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16[/FONT]

OK, so I booted into Fedora and typed "hdparm /dev/hdd" and got:

 HDIO_GET_MULTCOUNT failed: Invalid argument
 HDIO_GETGEO failed: Invalid argument

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

Looks good to me, except for the invalid argument things.  Then I rebooted into Ubuntu and typed "hdparm /dev/hdd" and got:

 HDIO_GETGEO failed: Invalid argument

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)


So in desparation, I typed the appropriate hdparm command to turn on IO_support to 32-bit, unmaskirq to 1, and using_dma to 1.  That didn't work either. :confused: 

Does anyone out there have any ideas on why Ubuntu and FC3 treat my DVDROM drive so differently?







Here are some other stats, in case they help:

root@tivo:/proc/ide/hdd# cat /proc/ide/hdd/settings
name                    value           min             max             mode
----                    -----           ---             ---             ----
current_speed           66              0               70              rw
dsc_overlap             1               0               1               rw
init_speed              12              0               70              rw
io_32bit                0               0               3               rw
keepsettings            0               0               1               rw
nice1                   1               0               1               rw
number                  3               0               3               rw
pio_mode                write-only      0               255             w
unmaskirq               0               0               1               rw
using_dma               0               0               1               rw

root@tivo:/proc/ide/hdd# cat /proc/ide/hdd/driver
ide-cdrom version 4.61

root@tivo:/proc/ide/hdd# cat /proc/ide/hdd/model
IDE DVD-ROM 16X

---

### Post by izm81 on 2005-12-27
This is probably a stupid question, but did you unmount/remount or eject/insert your disc after making the changes?  And did you try *just enabling DMA* or other non-exhaustive combinations of the options?

---

