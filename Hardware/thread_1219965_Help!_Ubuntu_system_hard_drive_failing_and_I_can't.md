---
title: "Help! Ubuntu system hard drive failing and I can't figure out why!"
date: 2009-07-22
forum: Hardware
---

### Post by runesvend on 2009-07-22
Hello all.

This all started while trying to resume from a suspended Linux session on Jaunty. I received errors similar to these and I didn't get any further (note: these messages are taken from another computer booted up via a jaunty Live CD while the hard drive in question is attached via USB in an external hard drive box):

```
[  133.804030] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  133.804037] ata3.00: cmd ca/00:08:3f:00:60/00:00:00:00:00/e2 tag 0 dma 4096 out
[  133.804038]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  133.804041] ata3.00: status: { DRDY }
[  133.804048] ata3.00: hard resetting link
[  134.124010] ata3.01: hard resetting link
[  139.640010] ata3.00: link is slow to respond, please be patient (ready=0)
[  143.840010] ata3.00: SRST failed (errno=-16)
[  143.850602] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  143.850612] ata3.01: SATA link down (SStatus 0 SControl 300)
[  143.850617] ata3.00: link online but device misclassified, retrying
[  143.850622] ata3.00: hard resetting link
[  144.168018] ata3.01: hard resetting link
[  149.648013] ata3.00: link is slow to respond, please be patient (ready=0)
[  153.904009] ata3.00: SRST failed (errno=-16)
```

I then tried booting up from a Live CD which produced the same errors. Only detaching the hard drive from my system and booting up via the Live CD worked. However, I tried booting up with the Live CD again today and now it works. Right now I'm sitting on a laptop (not the computer which originally produced the error) with the hard drive attached via an external hard drive box with USB running from a Jaunty Live CD.

When trying to mount the volumes on the - hopefully not broken, but seemingly not functional - hard drive, I get an error in nautilus suggesting to take a look at the dmesg output, which is:

```
[ 1466.476404] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1466.476417] sd 5:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1466.476428] sd 5:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1466.476439] end_request: I/O error, dev sdb, sector 65
[ 1466.476475] EXT3-fs: unable to read superblock

```

When trying to run fsck on the whole drive or individually on each partition I receive the following messages (note: the drive is not displayed in /etc/mtab as being mounted):

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sdb1
ubuntu@ubuntu:~$ sudo fsck /dev/sdb2
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/sdb3
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/sdb4
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb4
Could this be a zero-length partition?

```

GParted won't even show my hard drive as a selectable device. And this is the output of fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

Unable to read /dev/sdb

```

Here is what smartctl has to say:

```
ubuntu@ubuntu:~$ sudo smartctl --all /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: WDC WD50 00KS-00MNB0      Version:     
Device type: disk
Local Time is: Wed Jul 22 13:53:26 2009 UTC
Device supports SMART and is Enabled
Temperature Warning Disabled or Not Supported
SMART Health Status: OK

Error Counter logging not supported
Device does not support Self Test logging

```

I'm attaching the two versions of /var/log/syslog that I have. The first file is called "syslog-originalcomp-livecd-satacntrlr" and is the syslog file from booting up my own computer (the computer on which the error appeared originally) with a Live CD while the drive in question is attached to the computers SATA controller (which it had been all the time while it was functioning).
The other file I'm attaching is the syslog file of the laptop I'm currently sitting at, to which the hard drive is attached via USB sitting in an external hard drive box. This file is called "syslog-laptop-livecd-usbdrive".
Both the files are contained in "syslogs.tar.gz".

I'm really hoping someone can help me. What can I do?

Thanks in advance!

---

### Post by runesvend on 2009-07-22
Hmm. It seems I get a different error depending on which partition I try to open and read while running the Live CD (I am back at my own computer now). The drive is connected to the SATA controller.

Here is what happens when trying to open my root partition (dmesg output):

```
[ 2130.815495] sd 2:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2130.815500] end_request: I/O error, dev sdb, sector 943208282
[ 2130.815510] EXT3-fs: unable to read superblock

```

My home-partitions opens up fine without errors. But nautilus displays the content of certain folders as empty, when I know they are not. And trying to copy files results in this:

```
ubuntu@ubuntu:~$ sudo cp /media/disk-1/john/Music/*.* /home/ubuntu/Desktop/
cp: reading `/media/disk-1/john/Music/4475427.usf': Input/output error
cp: reading `/media/disk-1/john/Music/81792844.key': Input/output error
ubuntu@ubuntu:~$ dmesg | tail
[...]
[ 2251.407170] sd 2:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2251.407175] end_request: I/O error, dev sdb, sector 102121535
[ 2251.407610] sd 2:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2251.407614] end_request: I/O error, dev sdb, sector 102121543
ubuntu@ubuntu:~$ 

```

Trying to open the last partition gives the same error as the first (root) partition:

```
[ 2305.713957] sd 2:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 2305.713962] end_request: I/O error, dev sdb, sector 157292417
[ 2305.713972] EXT3-fs: unable to read superblock

```

So is my drive just dying or what? It's from Januray 2007, so it's only 2½ years old. But I guess it's possible.

Any ideas?

---

