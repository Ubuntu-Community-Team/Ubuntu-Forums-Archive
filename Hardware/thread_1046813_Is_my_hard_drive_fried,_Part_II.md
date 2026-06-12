---
title: "Is my hard drive fried, Part II"
date: 2009-01-21
forum: Hardware
---

### Post by jmc1 on 2009-01-21
Hi again! Last time I [posted here]("http://ubuntuforums.org/showthread.php?t=1038291"), my laptop hard drive had suddenly stopped being seen by the OS and it could only boot to BusyBox (I think that was what it was). A simple command that you guys suggested fixed the issue easily, but the fix only lasted for about 1 boot, sadly. It has come up with the same read errors, but when typing "sudo fsck /dev/sda1" it said it couldn't read it and asked me if it might have been a zero-length partition.

I've heard of the Seagate drive failures, and my drive is a Seagate, but I bought it a year ago and its serial number isn't on Seagate's craplist.

Now what do I do? I should have copied everything off the first time I got it to boot :(

---

### Post by jmc1 on 2009-01-21
Below are the commands I ran, based on what I found online to try to fix it, and the results.

```
sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

sudo mke2fs -n /dev/sda1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type = Linux
Block size=4096 (log=2)
Fragment size = 4096 (log=2)
9412608 inodes, 37650327 blocks
1882516 blocks (5.00%) reserved for the super user
First data block =0
Maximul filesystem blocks=0
1149 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 4096000, 7962624, 11239424, 20480000, 23887872
```

---

### Post by jmc1 on 2009-01-26
Nobody knows how to fix this? This stinks, I had all my data backed up on that thing :(

---

### Post by electrogeist on 2009-01-27
I am not sure.. but if I suspect a drive to be having hardware issues the first step is to try to get the data off it ASAP.  

If you can't mount it for normal copying you can try to DD an image to another drive

dd if=/dev/sda1 of=/path/with/lotsa/freespace/drive.image

and try to work with the image instead of the dying drive... mounting the image will require the "-o loop" option

you might try another system, another os, and another CABLE

and a google query such as 
http://www.google.com/search?q="fsck.ext2%3A+Attempt+to+read+block+from+filesystem+resulted+in+short+read+while+trying+to+open"&spell=1

whatever you do, have another drive ready to copy data to as soon as you can

---

### Post by Squid Spectre on 2009-01-27
If worse comes to worse you may just boot from the live CD and mount the drive then copy to some other medium (network drive, USB HDD, or likewise.) I've saved more than a few gigabytes of backed up data that way using BackTrak or Ubuntu.

---

### Post by jmc1 on 2009-01-30
Well, got another problem apparently: I tried to boot off the Live CD, but now it has the same problem as the normal install and even that goes into a busybox thing now. I tried a GParted ISO but the screen just blanks. It seems to be preventing every Linux distro I throw at it from booting now, which throws a wrench in those plans :(

Who knows, maybe my Vista DVD will boot...

(edit) Yep, the Vista DVD booted and it does see the partitions. I may yet have to go back to the dark side just to get a working system :|

---

### Post by jrusso2 on 2009-01-30
This is why seagate makes hard drive diagnostic tools.  Check your hard disk first.

[http://www.seagate.com/www/en-us/support/downloads/seatools/](http://www.seagate.com/www/en-us/support/downloads/seatools/)

---

### Post by jrusso2 on 2009-01-30
> **jrusso2 said:**
> This is why seagate makes hard drive diagnostic tools.  Check your hard disk first.

[http://www.seagate.com/www/en-us/support/downloads/seatools/](http://www.seagate.com/www/en-us/support/downloads/seatools/)

How old a hard drive is doesn't mean alot until its over 3 years old.

I have had drives last a week brand new, and some are still going after 8 years.

---

### Post by jmc1 on 2009-01-30
> **jrusso2 said:**
> This is why seagate makes hard drive diagnostic tools.  Check your hard disk first.

[http://www.seagate.com/www/en-us/support/downloads/seatools/](http://www.seagate.com/www/en-us/support/downloads/seatools/)
Those tools don't exactly work when I don't have an operating system that will successfully boot.

---

