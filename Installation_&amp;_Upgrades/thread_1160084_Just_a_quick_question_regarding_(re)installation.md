---
title: "Just a quick question regarding (re)installation"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Scarlath on 2009-05-15
Hello ... again! ;)

So I've come to the point when I'm installing Ubuntu 9.04 as it's working better than my existing 8.10 installation. However, when I get to the partitioner it all gets weird. Let me explain: 

1. I get to the partitioner and delete the existing 8.10 partitions (/, /home, and swap).
2. I create a new /, /home and swap. 
3. Now, this is where it's weird. It says that the root partition already got files in it (=it shows an amount of space used) and the "format"-option unchecks itself. Is this because I already had an existing root partition? I should check the "format"-box, right? (... and the same goes for the /home's and /swap's "format"-box, right?) I want to completely remove 8.10 and all of my saved files before installing 9.04. I want nothing from my old installation left on 9.04. 

Thanks in advance!

---

### Post by dstew on 2009-05-15
A couple of thoughts...

After you delete the 8.10 partitions, you did "Apply", and then gparted shows that region as unallocated space, correct? And then you attempt to create new partitions out of unallocated space.

When does it give you the information that the partition has files on it? Is it when you create the partition, or when you assign it to the root mount point? Or, as usual, you probably do both at once.

Try creating the partition first, then editing the partition to put in the mount point and file system as a separate step. If that doesn't help, it might be that the disk has some bad sectors on it that are confusing gparted. You might try to check the partition with [fsck]("http://linux.die.net/man/8/fsck").

---

### Post by Scarlath on 2009-05-15
I am not using GParted or anything (sorry if I wasn't clear enough on that), I'm doing this inside of the actual installer. I just assumed that the partition has files on it since it tells me that there's used space on it...

I deleted the partitions by pressing on them once and then choosing "delete" in the installation process, then I created the other partitions out of the "free space" (cant remember exactly what it said, typing this from Windows) that appeared once they were gone. I assign the mount point and create the partition in the same step. 

Could it be that the partitions are almost exactly the same as before?

Can't I just tick the format-box during the installation? I mean, does that not technically mean that the partition is formatted and then the root is installed there? Isn't that what I'm trying to achieve (sorry, I do not know a lot about these type of things)?

---

### Post by leilton on 2009-05-15
Going to show what a complete novice I am.   Have been running SUSE now for some little while, and mentioned this to a friend,who showed my the ubuntu on his laptop, seems to function better than my SUSE.   My problem is,apart from being a fool, is neither of us knows if,when I install ubuntu,it will over write suse,or if I will be left with two systems on my primative laptop.   Is old and being used to find best before it meets its maker.   And please no hysterical laughter at the back.   Any advice would be appreciated

---

### Post by Scarlath on 2009-05-15
Bump! Doubt anyone will check the second page and I'd love to get this up and running today :)

---

### Post by Kevbert on 2009-05-15
With the Ubuntu installer select manual partitioning and remove/delete all of the old partitions you no longer require. Now make a new partition equal to twice your RAM for the swap file. Set the remaining space as a new (system) partition formatted to ext3 and mounted /
Make sure that the format box of the system partition is ticked. Now continue the install. The disks will show up as being partly used for the file allocation tables (future file and directory info will be stored here).
If you are unable to format these new partitions with the installer than it may be that you have a faulty CD (have you burnt this yourself ? checked the CD integrity from the boot menu ?)

---

