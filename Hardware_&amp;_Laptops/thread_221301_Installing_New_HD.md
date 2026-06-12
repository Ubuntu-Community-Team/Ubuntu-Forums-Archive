---
title: "Installing New HD"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by outtacontrol on 2006-07-22
I am running Dapper, and I'm interested in installing a 2nd hard drive.  I haven't installed a new HD on an Ubuntu system before, and was wondering if ubuntu will automatically recognize the new drive.  How will I configure the drive to be used by Ubuntu?

Much thanks!

outta

---

### Post by gerbman on 2006-07-22
There is a lot of info for doing this. Examples include [this]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c") and [this]("http://www.psychocats.net/ubuntu/mountlinux.html").

---

### Post by x64Jimbo on 2006-07-23
I'm having problems with a new hard disk installation. 
My current drive is a 160GB, and the new one(s) is 2x320GB in a RAID Mirror. Obviously I would like to resize the new partitions to allow for more storage than I had before, but no amount of effort has been enough to effectively create new partitions in the new device, and image the partitions over using partimage without basically having the new partitions look like they're the same size as the old ones. 
Example I:
My original root partition was 30GB, but I soon realized that I don't need anywhere near that size for root. So I tried to change it after imaging (it won't even run the imaging process if the target partition is smaller than the original partition, even if it wasn't used all the way), and it wouldn't let me resize below 30GB. 
Example II: 
My original home partition was only 20GB, but I have realized that 20GB is not nearly enough. So I decided to bump it up to 60GB. Well, when I restore the partition from an image I took from the other hard drive, I have a 60GB partition, but gparted says that 40-something GB are in use already. How is this possible? The original partition was less than that. How can the data take up that much space? I even checked, and there are no duplicate files/directories.
A few facts that might be useful:
Hard disks are all SATA
all filesystems are jfs
I'm using the Xubuntu LiveCD because it's light on RAM usage and I can install partimage from the universe repos if I enable them in the LiveCD's sources.list. -- None of the hard disks in question are currently being used for running an operating system. 

Any help would be greatly appreciated.

[edit]
I found out that jfs partitions cannot be shrunk. (neither can xfs, for that matter) Well, that's the last time I use jfs! I'm going to try out reiserfs now. I'm using a tool called convertfs to convert my jfs partition over to reiserfs. It's pretty nifty. :)
[/edit]

---

