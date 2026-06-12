---
title: "HDD Not Accessible"
date: 2009-11-16
forum: Hardware
---

### Post by ShroudedCloud on 2009-11-16
Okay, so I was watching some videos the other day because of a really bad rainstorm. I'm right in the middle of one when the power drops out suddenly. Thing is, when I rebooted, I went to mount the drive (it's a secondary one) and it gives me an error message and won't allow me to mount it. Normally, it wouldn't be an issue, because I would just format it and be done, but, this one has some irreplaceable data on it that I would greatly prefer not losing.

I contacted some friends for help, and did 'fsck' and then the command it suggested after to no avail. I even did the follow up that that command suggested with no results obtained from doing so.

Any suggestions?

**_Relevant Data_**
Error Message:
```
UNABLE TO MOUNT DATA: Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
fsck RESULTS:
```
$ sudo fsck /dev/sdb
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by amishphysicist on 2009-11-30
I got this and simply reformatted the drive with gparted. sudo apt-get install gparted, sudo gparted, you're done!  Hopefully there's nothing on the drive you need, otherwise, try pulling everything off on a windows box first.

---

### Post by Some Penguin on 2009-11-30
> **ShroudedCloud said:**
> 
**_Relevant Data_**
Error Message:
```
UNABLE TO MOUNT DATA: Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```fsck RESULTS:
```
$ sudo fsck /dev/sdb
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Observation:  You're running fsck on a drive, not a partition (e.g. /dev/sdb1).  Do the latter.   fsck stands for "filesystem check" -- one filesystem at a time.

---

### Post by aav4bz on 2009-12-07
Hi ShroudedCloud--sorry to hear of your troubles. However, I have a different story about changing around hard drives, but with the same disasterous results as you. I've scoured the blogs looking for clues to try out, but nothing has worked for me yet.  My Ubuntu partition will not mount, in windows or from a live CD, while the other adjoining partitions will mount just fine. I've tried fetching BU superblock numbers, but none work. Incidently, my sdb2 is the problem, but Gparted and some other terminal efforts wouldn't open 'er up![B]
[/B]
I'm anxious to see if there's someone with a practical solution that will allow saving the partition contents.
Good luck--CD

---

### Post by aav4bz on 2009-12-08
Just after posting my last comment, I came across this post that may fix your problem. It would've worked for me, but none of my partitions will open now which most likely equals a busted HDD

try this:  
[http://ubuntuforums.org/showthread.php?t=1245536&highlight=bad+superblock](http://ubuntuforums.org/showthread.php?t=1245536&highlight=bad+superblock)

Sorry if this isn't properly posted.  Good luck--CD

---

### Post by ShroudedCloud on 2010-03-05
> **Some Penguin said:**
> Observation:  You're running fsck on a drive, not a partition (e.g. /dev/sdb1).  Do the latter.   fsck stands for "filesystem check" -- one filesystem at a time.

Sorry, I'd forgotten to check on this thread. You were absolutely right, I was an idiot and typed the wrong command. I followed your advice and it works perfectly fine now. Thank you so much.

---

### Post by slickytail on 2011-05-17
if i was to try this with an ipod would it work?

---

