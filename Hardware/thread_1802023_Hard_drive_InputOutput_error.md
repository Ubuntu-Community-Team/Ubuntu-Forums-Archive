---
title: "Hard drive Input/Output error"
date: 2011-07-11
forum: Hardware
---

### Post by downwardspiral on 2011-07-11
Almost all of my normal methods have been completely thwarted by this hard drive. It's a Samsung _[HM320JI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152111") _ and suffers from bad sectors. A little back story. My friend wanted me to backup his documents and format his hard drive with Ubuntu since he was sick of Vista. The laptop's hard drive wouldn't even boot, so I tried a livecd but the disk drive appears to be sluggish so I removed the hard drive and put it into my desktop at home. I boot up Ubuntu from a pendrive and mount the hard drive and start off with a cp -rv /media/xxxxx/Users/xxxx /media/backupdrive/blah. You get the idea. After 5 minutes of backing up I get a Input/Output error on about 100 files then the hard drive auto unmounts and cannot be found using fdisk -l, forcing me to reboot to try again only to run into the same headache. I also tried launching from the Vista startup disk and repairing it with chkdsk /r but that quit at 10% with no errors, right as it hit step 2 of 5. Is anyone here knowledgeable enough about fsck that they can help me with it? Or is there an easier route?

---

### Post by downwardspiral on 2011-07-11
Anyone there?

---

### Post by downwardspiral on 2011-07-11
This is the result of a gparted check.

[HTML]
GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
    Check and repair file system (ntfs) on /dev/sda1  00:00:01    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             path: /dev/sda1
start: 2048
end: 597694463
size: 597692416 (285.00 GiB)          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:01    ( ERROR )             ntfsresize -P -i -f -v /dev/sda1             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 306018513408 bytes (306019 MB)
Current device size: 306018516992 bytes (306019 MB)
Checking for bad sectors ...
Bad cluster: 0x9c4908 - 0x9c4908    (1)
Bad cluster: 0x9c4a82 - 0x9c4a82    (1)
Bad cluster: 0x9c4b32 - 0x9c4b32    (1)
Bad cluster: 0x9c4be1 - 0x9c4be1    (1)
Bad cluster: 0x9c4c90 - 0x9c4c90    (1)
Bad cluster: 0x9c4d40 - 0x9c4d40    (1)
Bad cluster: 0x9c4def - 0x9c4def    (1)
Bad cluster: 0x9c4e9e - 0x9c4e9e    (1)
Bad cluster: 0x9c5019 - 0x9c5019    (1)
Bad cluster: 0x9c50c8 - 0x9c50c8    (1)
Bad cluster: 0x9c5177 - 0x9c5177    (1)
Bad cluster: 0xab4bcb - 0xab4bcb    (1)
Bad cluster: 0xd339c2 - 0xd339c2    (1)
Bad cluster: 0xd45992 - 0xd45992    (1)
Bad cluster: 0xd45a3e - 0xd45a3e    (1)
Bad cluster: 0xd45aeb - 0xd45aeb    (1)
Bad cluster: 0xd45b97 - 0xd45b97    (1)
Bad cluster: 0xd45d0c - 0xd45d0c    (1)
Bad cluster: 0xd46117 - 0xd46117    (1)
Bad cluster: 0xd4628b - 0xd4628b    (1)
Bad cluster: 0xd46338 - 0xd46338    (1)
Bad cluster: 0xd463e4 - 0xd463e4    (1)
Bad cluster: 0xd46491 - 0xd46491    (1)
Bad cluster: 0xd4653d - 0xd4653d    (1)
Bad cluster: 0xd465ea - 0xd465ea    (1)
Bad cluster: 0xd46696 - 0xd46696    (1)
Bad cluster: 0xd46743 - 0xd46743    (1)
Bad cluster: 0xd4cb8c - 0xd4cb8c    (1)
Bad cluster: 0xd9c265 - 0xd9c265    (1)
Bad cluster: 0xdaae0e - 0xdaae0e    (1)
Bad cluster: 0xdade0e - 0xdade0e    (1)
Bad cluster: 0xdadebb - 0xdadebb    (1)
ERROR: This software has detected that the disk has at least 32 bad sectors.
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason.   *
* The reliability of the disk may stay stable or degrade fast. We suggest  *
* making a full backup urgently by running 'ntfsclone --rescue ...' then   *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************
             ========================================
    Check and repair file system (ntfs) on /dev/sda2    ========================================

[/HTML]

---

### Post by downwardspiral on 2011-07-11
$ sudo ntfsclone --rescue /dev/sdb -o backup
> 
ntfsclone v2.0.0 (libntfs 10:0:0)
ERROR(22): Opening '/dev/sdb' as NTFS failed: Invalid argument
Apparently device '/dev/sdb' doesn't have a valid NTFS. Maybe you selected
the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)?


---

### Post by tgalati4 on 2011-07-11
Could be the drive controller going bad.  It heats up after a few minutes of use, resulting in errors.  Don't try repairing with fsck, but put it in a freezer bag with a dry paper towel and stick in the freezer for a hour.  Then pull out and quickly try to copy files.  Keep note of where you left off, since you might have to repeat this procedure several times.

Trying to "repair" a drive with fsck with a controller problem will simply mess up the drive more.

---

### Post by downwardspiral on 2011-07-11
> **tgalati4 said:**
> Could be the drive controller going bad.  It heats up after a few minutes of use, resulting in errors.  Don't try repairing with fsck, but put it in a freezer bag with a dry paper towel and stick in the freezer for a hour.  Then pull out and quickly try to copy files.  Keep note of where you left off, since you might have to repeat this procedure several times.

Trying to "repair" a drive with fsck with a controller problem will simply mess up the drive more.


I'll try this now.

---

### Post by iisjman07 on 2011-07-12
You want to clone the drive onto a working medium. You'll probably have most success with ddrescue, as it can do a reverse clone and hopefully get back as much data as possible.

---

### Post by downwardspiral on 2011-07-12
The ddrescue manual told me this:

> IMPORTANT! Never try to repair a file system on a drive with I/O errors; you will probably lose even more data.     Does anyone know how I should proceed from here? Also, the freezer option stopped working this morning, now I only get I/O errors even if it's the first minute of being plugged into the computer.

---

### Post by downwardspiral on 2011-07-14
Same problem, no changes. :(

---

### Post by btbaus on 2011-09-06
did u ever solve this problem? my disk results in a input/output error when running the dd command.

---

### Post by downwardspiral on 2011-09-21
No, I was never able to solve this problem. I think the hard drive needle was off balance in my case.

---

### Post by Trinity1976 on 2011-10-30
I've been having a similar problem. I wonder if anyone can help.

A couple of weeks ago, the computer started crashing, generally whilst watching a video file.

Now I'm having serious trouble booting. I have a 1TB hard-drive with the OS installed on a 30GB partition, about 50GB of unused space, and the rest of the drive is one big partition with data.

Sometimes the computer doesn't see the drive, other times it gets part-way through booting up then hangs, and other times it manages to boot up but crashes after a few minutes of use. Disk Utility says the disk has some bad sectors (despite being quite new).

I've tried booting from the live CD but on the one occasion the computer could actually 'see' the drive, the computer crashed again partway through fsck.

So yesterday I got hold of an old, but unused, 80GB drive and installed the OS on that, booted up, no problems. Started running fsck on the large partition on my 1TB drive, several hours later in the middle of the night it all went quiet and I found that I had an unresponsive purple screen.

So this morning, I am experiencing the same problems I have had all along, even though the operating system is now on a different (healthy) drive. It booted up then crashed a few minutes later, complaining about input/output errors, now it won't boot.

So if it was a drive problem, how come it still has issues with a brand new install on another drive? Any ideas?

---

### Post by downwardspiral on 2011-10-31
Sounds like it could be a bad motherboard or cable. Try switching out the cable and if the error continues on the new HD, try putting the HD In a new computer and see if the problem persists. If not, you may need a new motherboard. Because to me that sounds a lot like a hardware problem, and a bad one at that.

---

### Post by jonnyboysmithy on 2011-11-12
Also make sure things aren't getting too hot like the ram or the cpu etc, I had some trouble recently and that was the cause. :)

---

