---
title: "Installation Help!"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by buyuden on 2009-01-07
I'm trying to install Ubuntu 8.1 and I'm a new Linux user. Currently, I have three partitions on my PC. One is a empty 30 Gig NTFS drive that I want to use exclusively for Ubuntu. Right now I'm installing and I have few questions.

First of all, it seems like I need to edit the partition format into either ext2 or ext3. which one should I use?

Secondly, what is a mount point and where should i set it as

Thanks

---

### Post by UriahHeap on 2009-01-07
I had the same problem.  I have screwed up my pc more times than I can count trying to get the partitioning right for Linux.  I solved my problem by installing a new hard drive in the tower, disconnected the power cable on the Windopes hard drive & used the new hard drive for Ubuntu.  Using this method allows the Linux install to use the entire drive automatically.  When I want to boot to Windopes, I simply change the boot device at startup.  I do have Ubuntu on the first boot device so it is the os I am trying to use for almost everything.

The one "problem" I have is I can't get Linux to auto load my music from a third drive so I have to copy it to the Linux drive.  But I don't lose my music when something goes wrong!

---

### Post by fajarhp on 2009-01-07
for linux partition, you should choose "ext3",and don't forget you must make "swap partition" for recommendations, the volume of swap partition is two times of memory RAM. for example, if you have 256 mb of RAM you should make 512 MB of swap file.

for mount point, select on your linux partition (I mean your "ext3") choose "/".

---

### Post by mikewhatever on 2009-01-07
ext3 is the default

> For files and directories in a Unix filesystem to be accessible that filesystem must be Mounted using the mount(1m) command. The action of mounting a filesystem simply connects that filesystem to the existing directory structure. Under Unix there are no drive letters or volume names as in DOS on VMS, nor are there commands to change which filesystem you are using - simply 'cd'ing to a directory may change that...

read here for more [http://andrew-gray.com/unixfaq/filesystem.shtml](http://andrew-gray.com/unixfaq/filesystem.shtml)

---

### Post by kranny on 2009-01-07
The advantage of ext3 is that it has a journal, yes, and therefore it is a good choice for partitions with write access.

However, journaling imposes a (normally negligible) performance penalty on the file system, and it takes more space. For these two reasons I use ext2 for read-only partitions, like my /boot partition, and ext3 for just about everything else.

For applications handling huge files (bigger than 100 MB), such as multimedia streaming servers, I recommend XFS or JFS.

And the mount point Just put a '/' on your to-be root partition

---

