---
title: "Problem writing to my flashcard"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by unperson on 2006-02-20
I have an SD flashcard that I use with my USB flashcard reader.  I just started using this on my Ubuntu 5.10 system this weekend, and it was working beautifully.  It would automount when I plugged it in, I could read and write to the drive, and it would unmount cleanly.  I did this several times.

This morning when I plugged the card in everything acted normally until I tried to transfer files to it, at which point it told me that I did not have permission to write to the folder (on the flashcard).  This new behavior does not make any sense, since AFAIK I have not changed any relevant settings!  The mount point (and all directories on the mounted volume) shows me as the owner with rwx permissions.  Looking in /etc/mtab, I see the drive is mounted read-only

```
/dev/sdc1 /media/flashcard vfat ro,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```


I tried to re-mount it read-write in the terminal with

```

sudo umount /media/flashcard/
sudo mount -t vfat -w /dev/sdc1 /media/flashcard

```

but I get the following error and the drive does not mount

```

mount: block device /dev/sdc1 is write-protected but explicit `-w' flag given

```

So, how can I fix this so I can write to my flashcard again?  What does it mean about the card being "write-protected" (clearly something other than file permissions or mount settings)?  Why did this behavior spontaneously change?  The first question is the most important, of course, but I'm curious about any of the above.

Thanks in advance!

---

### Post by unperson on 2006-02-20
A little more information.  When I plug the card into the reader, I get the following from dmesg:

```

Feb 20 21:05:18 localhost kernel: [ 3450.877593] sdc: Write Protect is on
Feb 20 21:05:18 localhost kernel: [ 3450.877619] sdc: Mode Sense: 02 00 80 00
Feb 20 21:05:18 localhost kernel: [ 3450.877631] sdc: assuming drive cache: write through
Feb 20 21:05:18 localhost kernel: [ 3450.892585] SCSI device sdc: 1002496 512-byte hdwr sectors (513 MB)
Feb 20 21:05:18 localhost kernel: [ 3450.918449] sdc: Write Protect is on
Feb 20 21:05:18 localhost kernel: [ 3450.918473] sdc: Mode Sense: 02 00 80 00
Feb 20 21:05:18 localhost kernel: [ 3450.918485] sdc: assuming drive cache: write through
Feb 20 21:05:18 localhost kernel: [ 3450.918504]  /dev/scsi/host1/bus0/target0/lun2: p1
Feb 20 21:05:19 localhost kernel: [ 3451.785103] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

I would imagine that the line, "sdc: Write Protect is on" is related to the problem.  Why this would have changed, however, I have no idea.  The card doesn't seem to have an obvious physical write-protect switch, nor does the drive.  Or is it possible this is still just a software issue (with hotplug or the usb-storage driver or something)?

Following some of the stuff on [this page](http://www.linuxjournal.com/article/6867), I tried plugging it in, letting it mount, and then using the command

```

sudo mount -o rw,remount /media/flashcard

```

to remount it read-write.  That *appeared* to work.  /etc/mtab showed the drive now read-write, and in the terminal I used the rm command to delete one of the files on the flashcard with no errors.  However, appearances were deceptive.  I umounted, unplugged the card, and then plugged it back in again.  When I looked in the directory, the file had not actually been deleted.  Looking in dmesg I found

```

[ 1172.172644] SCSI error : <0 0 0 2> return code = 0x8000002
[ 1172.172672] sdc: Current: sense key: Hardware Error
[ 1172.172685]     Additional sense: Data phase error
[ 1172.172722] end_request: I/O error, dev sdc, sector 106
[ 1172.172743] Buffer I/O error on device sdc1, logical block 43
[ 1172.172760] lost page write due to I/O error on sdc1
[ 1172.180617] SCSI error : <0 0 0 2> return code = 0x8000002
[ 1172.180642] sdc: Current: sense key: Hardware Error
[ 1172.180654]     Additional sense: Data phase error
[ 1172.180690] end_request: I/O error, dev sdc, sector 107
[ 1172.180711] Buffer I/O error on device sdc1, logical block 44
[ 1172.180725] lost page write due to I/O error on sdc1
[ 1172.188608] SCSI error : <0 0 0 2> return code = 0x8000002
[ 1172.188632] sdc: Current: sense key: Hardware Error
[ 1172.188644]     Additional sense: Data phase error

...[much more]...

[ 1172.254636] end_request: I/O error, dev sdc, sector 356
[ 1172.260562] SCSI error : <0 0 0 2> return code = 0x8000002
[ 1172.260588] sdc: Current: sense key: Hardware Error
[ 1172.260601]     Additional sense: Data phase error
[ 1172.260637] end_request: I/O error, dev sdc, sector 554
[ 1172.268573] SCSI error : <0 0 0 2> return code = 0x8000002
[ 1172.268599] sdc: Current: sense key: Hardware Error
[ 1172.268612]     Additional sense: Data phase error
[ 1172.268648] end_request: I/O error, dev sdc, sector 175050

```

So it looked like that remount didn't do quite what I hoped.  I still have no idea what is going on really.  I don't know anything about write-protection features of flash memory, and I'm not even positive that's the problem.  

The card in question here is a SimpleTech 512 MB SD card.  I also tried my 128 MB MMC card, and it also appears to mount read-only and show "write-protected" in dmesg.  I've used these cards for a while and never had this problem to my knowledge.  The card reader I'm using is a SanDisk 12-in-1, from /proc/scsi/usb-storage/1

> 
 Host scsi1: usb-storage
       Vendor: SanDisk
      Product: ImageMate 12 in 1 Reader/Writer
Serial Number: 0300492815
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:


Any help would be appreciated.

---

### Post by unperson on 2006-02-25
Since I last posted, I attempted to reformat the partition on my flashcard using mkfs  and got the response, "mkfs.vfat: unable to open /dev/sdc1", and I tried to repartition the flashcard using fdisk, which only resulted in the message, "Unable to write /dev/sdc".

I also tried plugging the card reader into an OS X computer and read the card on there.  It also insists that the card is write protected and will not allow me to delete files, reformat, or repartition.

The only other variable would be the card reader, but for right now I don't have access to another card reader.  However, I should note that my mp3 player is still able to delete files from card.  It's alll very strange and I'm quite confused.

Help!  :confused:

---

### Post by Lothas on 2008-03-22
I'm having the same problem with Ubuntu 7.10... :(

---

