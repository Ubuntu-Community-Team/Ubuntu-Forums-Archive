---
title: "CD drive wont mount! Any Suggestions?"
date: 2008-07-08
forum: Hardware
---

### Post by NNNNNNNNNN1515 on 2008-07-08
I'm running ubuntu on my computer. I have four drives: one hard drive, a floppy drive, and two cd drives. One is a cd/dvd rom drive. The other is a cd-RW drive. Whenever I try to access a cd in either drive, file browser displayes the message **"Unable to mount location - no media in the drive"**. Problem is, there IS media in the drive. I ought know. I put it there! :mad:

I tried searching this forum for similar posts, and I found a few, but since I'm new to linux, they weren't much help. In all of them, however, I noticed that problems were diagnosed with information from fstab, and after reading up on the subject, I figured out how to read it in terminal. :)

So here is what my fstab says:
> 

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=a5716e71-cff2-4a12-be80-0ae76a3d2e49 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=33da9863-d8de-4021-a18c-c6ad9fe267b6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

I'm guessing scd0 and scd1 are my cd drives. fd0 is clearly my floppy drive. By process of elimination, I deduce sda5 to be my hard drive. Is this correct?

That's pretty much all I understand so far. Does anyone see anything wrong with this fstab report that could be preventing me from mounting my cd drives? Or has anyone had this error before? What should I do to get my cd drives to work? And don't spare on the lengthy technical discussions! I love learning new things about linux. :)

---

### Post by phidia on 2008-07-08
/dev/sda5 is the partition ubuntu is installed to-not the entire drive.
Your fstab seems ok from what I can tell.
Open a terminal and enter this > cdrecord -scanbus and maybe > cdrecord -checkdrive you might need to use sudo with those commands.
Post the output of that here.

---

### Post by NNNNNNNNNN1515 on 2008-07-08
Here is the output:

> normloman@normloman-desktop:~$ cd record -scanbus
bash: cd: record: No such file or directory
normloman@normloman-desktop:~$ cdrecord -scanbus
scsibus1:
	1,0,0	100) 'HITACHI ' 'DVD-ROM GD-5000 ' '0213' Removable CD-ROM
	1,1,0	101) 'OPTORITE' 'CD-RW CW4802    ' '150E' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
normloman@normloman-desktop:~$ cdrecord -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'OPTORITE'
Identification : 'CD-RW CW4802    '
Revision       : '150E'
Device seems to be: Generic mmc CD-RW.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R



BTW thanks for explaining dev/sda5 . I think I only have one partition that takes up the entire drive, but thats good to know for further reference :) !

So how about it. Does anyone recognize anything wrong yet, or have any suggestions?

---

### Post by NNNNNNNNNN1515 on 2008-07-09
I've been fooling around with different settings for a bit now. Still no answers.
Does anyone have any suggestions, or even know of a website with some more information on these sorts of problems?

I found out some more information BTW:

Apparently I can mount data cds, but I still can't recognize music cds. What could be causing this?

[B]Edit: Problem solved.

[http://mandrivausers.org/index.php?showtopic=4831](http://mandrivausers.org/index.php?showtopic=4831)

I didn't know music cds could not be mounted.

Thank you everyone that read and offered suggestions.[/B]

The cd I was using was just bad. I put in another music cd and it loaded on its own.

---

