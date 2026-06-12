---
title: "Recover Hard Drive or Image File"
date: 2013-11-19
forum: Hardware
---

### Post by mrjagdad on 2013-11-19
So here it is, my hard drive has crashed
Barracuda 7200.12
S/N: 9VP6LL1T
ST31000528AS
P/N: 9SL154-336
Firmware: CC3E
Date Code: 10424
Site Code: SU
Board #: 100536501 Rev A

I have read about replacing the system board.  I looked at the board
with a magnifying glass, did not see any burnt spots.

The system was running ubuntu 12.04

Before it completely died I was able to get an image file with ddrescue.
I have read numerous threads about trying to recover the file system,
However all my attempts have failed but I may not have performed the
correct steps.

The name of the file is image.  I have made a copy of the image file.

Running mmls I get this
$ sudo mmls -i raw -t bsd image
Invalid magic value (BSD partition table (magic #1) (Sector: 1) 0)

I tried foremost and was able to get some data off of it, .jpg, etc. However it is unorganized.
I would like to salvage the File System as there are a number of pictures on there that were
not backed up yet.

Now I am stuck, any help would be appreciated.

---

### Post by oldfred on 2013-11-20
Did you use BSD not standard ext4 for format? 

Never seen mmls before,  I just read man page
What does this show.
sudo mmls image

---

### Post by mrjagdad on 2013-11-20
When I run mmls against the image file I get this

$ sudo mmls image
Cannot determine partition type

Before the drive died this is the message I received
Dying hard drive
1.0 TB ATA ST31000528AS
Use Disk utilty see one partition 991 GB ext4
Disk FAilure is imminent
/dev/sdb

disk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1935388671   967693312   83  Linux
/dev/sdb2      1935390718  1953523711     9066497    5  Extended
/dev/sdb5      1935390720  1953523711     9066496   82  Linux swap /
Solaris

I created an image of /dev/sdb1 using ddrescue

$ sudo ddrescue -d -r3 /dev/sdb1 image ddrescue.log

The drive died before I could run successive ddrescues against it.

Bigger question, and I have tried a number of things.
How do you try to recover the file system against the image file.

---

### Post by oldfred on 2013-11-20
That says it was ext4. I have never used mmls, but specifying ext4, does it work?

sudo mmls -i raw -t ext4 image

Many, many years ago I lost backups to my dual floppy as a compressed image. Since then I have avoided any image or compressed file backup where possible and just backup files. Uncompressed images have more options to recover.

---

### Post by cathyhill on 2013-11-21
> **oldfred said:**
> That says it was ext4. I have never used mmls, but specifying ext4, does it work?

sudo mmls -i raw -t ext4 image

Many, many years ago I lost backups to my dual floppy as a [[COLOR=#272727]compressed image[/COLOR]]("http://www.rasteredge.com/dotnet-imaging/image-compression/"). Since then I have avoided any [[COLOR=#272727]imaging[/COLOR]]("http://www.rasteredge.com/dotnet-imaging/features.shtml") or compressed file backup where possible and just backup files. Uncompressed images have more options to recover.


You said **uncompressed images have more options to recover**, could you please give more information about that?

---

### Post by oldfred on 2013-11-21
That was just a comment that I just back up all my files as files. 
I use rsync and copy data to another drive. And regularly copy most important files to DVDs so I have some history in case I have modified something & backed it up, but want older copy. Then even a scratch on DVD may let me recover some files. Where a compressed image will often not uncompress as it cannot generate correct code for image.

       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

---

### Post by Ranko Kohime on 2013-11-21
I believe the issue might be that you have a full disk image, whereas mmls expects a partition image.  Perhaps this link will be of some help?

[How to extract a filesystem from a disk image]("http://nerdnotes.wordpress.com/2008/04/18/disk-image-wizardry/")

---

### Post by andyfied on 2013-11-22
Not that it relates to the disk image (which I think you have now), but if you **were **planning on swapping pcbs with another 7200.12, you will need to ensure it is the same model number. Then you would need to swap the ROM chip from the old board to the new one. (Soldering skills needed)

---

