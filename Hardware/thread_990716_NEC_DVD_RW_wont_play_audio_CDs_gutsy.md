---
title: "NEC DVD RW wont play audio CDs gutsy"
date: 2008-11-23
forum: Hardware
---

### Post by fenifur on 2008-11-23
I recently reinstalled my DVD RW.  BIOS recognizes DVD device.  I can boot a Live CD from this drive.  I can even play videos burned to DVD +R.  However, when I try to play an original audio CD I get the following error:

mount: block device /dev/hdb is write-protected, mounting read-only 
mount: wrong fs type, bad option, bad superblock on /dev/hdb, 
       missing codepage or helper program, or other error 
       in some cases useful info is found in syslog - try 
       dmesg | tail  or so

**dmesg | tail output:**

=>dmesg | tail 
[  221.397903] ide: failed opcode was: unknown 
[  221.398449] hdb: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00 
[  221.398452] end_request: I/O error, dev hdb, sector 1024 
[  221.398810] UDF-fs: No partition found (1) 
[  221.409991] hdb: command error: status=0x51 { DriveReady SeekComplete Error } 
[  221.409999] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 } 
[  221.410004] ide: failed opcode was: unknown 
[  221.410385] hdb: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00 
[  221.410389] end_request: I/O error, dev hdb, sector 64 
[  221.410926] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16

**output from lshw:**

*-cdrom

     description: DVD writer
     product: _NEC DVD_RW ND-3500AG
     physical id: 1
     bus info: ide@0.1
     logical name: /dev/hdb
     version: 2.16
     capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
     configuration: mode=udma2 status=ready

**entry in /etc/fstab:**

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

**check of links:**

=>ls -ltr /dev/dvd

lrwxrwxrwx 1 root root 3 2008-11-22 22:41 /dev/dvd -> hdb

=>ls -ltr /dev/cdrom

lrwxrwxrwx 1 root root 3 2008-11-22 22:41 /dev/cdrom -> hdb

Any help would be greatly appreciated.  I have three new CDs I need to convert to mp3s so I can move them several MP3 players.  :guitar:

---

### Post by Yezinki on 2008-11-23
NEC/Panasonic/Matshita drives have such issues/ buggy drives.

Is the Region code set or is it Region Free?

Do you own a OEM machine...what brand?

Regards,

Yezinki.

---

### Post by fenifur on 2008-11-23
I don't know if region is set?  How does one tell?

I built the computer.  The dvd drive was working fine the last time it was installed.  I pulled it because I had to pull data off another IDE HD on a PC that died.  When I reinstalled I starting having the problems described above.

---

### Post by fenifur on 2008-11-23
Ok.  I pulled the DVD drive to look at the jumper settings and I noticed one of the pins where the ide cable is connected was pushed in slightly.  I carefully pulled it out a little with needle nose pliers.  Success!  Thank God.  My next "fix" involved a hammer.  LET THERE BE ROCK!:guitar:

---

