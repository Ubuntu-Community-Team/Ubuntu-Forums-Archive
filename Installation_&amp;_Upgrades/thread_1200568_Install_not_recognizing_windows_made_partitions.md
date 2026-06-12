---
title: "Install not recognizing windows made partitions"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Shadow_Keeper on 2009-06-30
Hello!

Okay my first admission should be this is my first real experience in using Ubuntu, I have only had experience in using and installing Slackware before this. 

Right now here is the problem I am experiencing. I have two 160GB hard drives in my Dell XPS M1730, partitioned into two drives, one 265GB drive (for windows), and one 50GB drive (for Ubuntu). Originally it was just one partition, but I shrunk this to make a FAT32 partition for Ubuntu (yes I know this needs to be split into 2, to allow for a swap partition). The problem is when I run the latest version of Ubuntu (downloaded yesterday, put onto disk, booted and ran the install), it just shows my two 160GB drives, not the partitions. It also says they both do not have any operating system. I am sure if I did install onto one of these drives, it would remove my Windows and probably cause problems with my partition table. Any idea what the problem is, or how I can solve this? Thank you to everyone who takes time to read this, it is greatly appreciated. Thanks.

---

### Post by mcduck on 2009-06-30
One thing to try would be simply deleting the partition you made for Ubuntu (it's not going to be actually used anyway, as Ubuntu can't be installed on FAT or NTFS filesystems) and leaving that space as empty, unpartitioned space. Then Ubuntu's installer should detect the free space and give you option to use that for Ubuntu.

---

### Post by Shadow_Keeper on 2009-06-30
Thank your for your reply :). I tried this, but still Ubuntu simply sees the hard drives, not any of the partitions :(.

---

### Post by lindsay7 on 2009-06-30
Download Gparted from their web site and burn it to a disk. You can start you system with it. It will let you take a screen shot of your drive or drives. Post the screen shots on this forum and lets take a look at what you have going on here. You should be able to get some help from this info.

---

