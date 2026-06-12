---
title: "Trouble copying file to SD card in USB card reader"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by Kensey on 2007-02-12
A few days ago I bought a LinksKey USB SD card reader (LKA-CR811) and a SanDisk 1.0 GB SD card.  I formatted the card as FAT32 in Windows.  If I plug it into my laptop running Linux, it seems OK -- it shows up as a usbdisk and dmesg suggests things are more or less OK (it complains about the IO charset being utf8 and that not being recommended for a FAT filesystem, but everything else looks OK).  However, when I try to copy large files, after awhile I get "Error 'I/O Error' while copying <large file>"  It doesn't consistently do this at a particular offset.

The file in question is an 820-odd MB video file, and plays completely fine in mplayer.  Here are the points where the copy died in five successive attempts: 23.5 MB, 19.5 MB, 5.5 MB, 54.5 MB, 10.5 MB.

When the copy dies, dmesg shows:

[17183445.460000] sd 6:0:0:0: Device not ready: <6>: Current: sense key:
Not Ready
[17183445.460000]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>>
ASCQ=0xff
[17183445.460000] end_request: I/O error, dev sdb, sector 669129
[17183445.460000] sd 6:0:0:0: Device not ready: <6>: Current: sense key:
Not Ready
[17183445.460000]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>>
ASCQ=0xff
[17183445.460000] end_request: I/O error, dev sdb, sector 669369
[17183445.600000] end_request: I/O error, dev sdb, sector 937
[17183445.600000] FAT: FAT read failed (blocknr 688)
[17183445.644000] SCSI device sdb: 1984000 512-byte hdwr sectors (1016 MB)
[17183445.668000] sdb: Write Protect is off
[17183445.668000] sdb: Mode Sense: 03 00 00 00
[17183445.668000] sdb: assuming drive cache: write through

When I reboot my laptop into Windows, the same file copies completely fine onto the reader (I have an ext3 read driver installed in Windows XP) and I'm able to play the video without stutters or skips.  So I'm pretty sure the file itself, the reader and the card are all fine.

Is this happening because of the IO charset issue I'm being warned about when I mount the drive, or is it something else?  How do I fix it?

---

