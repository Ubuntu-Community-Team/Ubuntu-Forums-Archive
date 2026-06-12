---
title: "USB drive 'disappears' during use."
date: 2019-12-18
forum: Hardware
---

### Post by brian666 on 2019-12-18
Using Ubuntu 18 LTS 64-bit, all patches applied, PC is an AMD Phenom x2 6-core, 8 GB of RAM. I have an 8 TB USB 3.0 Western Digital drive attached, this drive AND the backup drive (same specifications) have a habit of 'disappearing' when in use. By that, I mean that I can be playing a video from the drive, all of a sudden the video will stop playing. When I try to investigate, a df still shows the drive connected with the correct usage details, but if I try to access the files on the drive, it's just like the drive wasn't connected, i.e. I can change into the directory which is the mount point, but there are no subdirectories or files visible if I try an ls -l  - this is not just playing videos, I was using Filezilla this morning and downloading into a directory on the drive, all of a sudden the download aborted with an error, same symptoms, the drive had disappeared again. 

I've tried different USB ports, and obviously the two drives have their own power supplies and cables, so that's not the answer. It's not a frequent occurrence, just often enough to be annoying. I did a test on the backup drive, wrote a program which created a multi-terabyte random access file and then just went back and forth through the file, writing and reading binary patterns, and it took about 30 hours for the problem to occur. The error codes from the program just gave me a 'no such file' status on one of the reads. 

Western Digital support is hopeless, the moment I mention Linux they throw a hissy fit and tell me that they can do nothing for me. I managed to get them to RMA one drive, but they've not managed to ship me a working replacement yet (third attempt in progress!) 

Afterthought: The drive is formatted as one humongous ext4 partition mounted at /multimedia, and yes, when I look at the df and ls output, it's as root, it's not some kind of permissions problem. 



Does anybody have any ideas, please?

---

### Post by TheFu on 2019-12-18
I use WD external USB3 disks only for backups for this reason alone.  Whenever USB connections are required, I use autofs to mount on-demand.

Some WD external drives have aggressive firmware settings to spin down the disks.  
A few models didn't provide control to the OS.
Many WD external enclosures can be shucked and plugged in internal to the computer via SATA ports.  Sometimes the inside HDD is a WD-Red.
The external enclosure might be lying about the HDD actually inside.  
Some of the internal disks are run at slower rpm in the enclosure than they would be inside a computer.  There are lots of rumors as to why WD might use a "Red" drive inside an external enclosure and sell it for $60 less than the "red" drive alone.  Your guess is as good as mine.

* see if there is any firmware update for the HDD. Some firmware updates can wipe the disk unexpectedly.
* see if **hdparm** can control the spin-down settings to be something you might prefer.

USB port connections can be flaky. I've had some with issues due to vibrations from computer fans.

That's all I have for blind ideas.

---

### Post by brian666 on 2019-12-18
ok, thanks. I'd have to rebuild the PC into a larger case to try to mount the drives internally - I'm out of hard drive enclosures. I'll try to investigate your other ideas.

---

