---
title: "Unable to reformat USB drive"
date: 2009-09-29
forum: Hardware
---

### Post by MedianMajik on 2009-09-29
I've tried reformatting some USB thumb drives and one in particular is giving me trouble.  I used Boot 'N Nuke it erase all old data before using Gparted to reformat the drive into ext3.

I received the following error:
GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ext3, 7.45 GiB) on /dev/sdb  00:00:21    ( ERROR )
     	
create empty partition  00:00:10    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 15631244
size: 15631182 (7.45 GiB)
set partition type on /dev/sdb1  00:00:10    ( SUCCESS )
     	
new partition type: ext3
create new ext3 file system  00:00:01    ( ERROR )
     	
mkfs.ext3 -L "Kingston Ext3" /dev/sdb1
     	
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdb1 is mounted; will not make a filesystem here!

========================================

---

### Post by MedianMajik on 2009-10-05
Anyone?

---

### Post by dummy910 on 2009-10-05
If this USB drive has the horrible "U3" system on it, here's what I did just a few weeks ago to get the isofs format off of it, and turn it into an ubuntu booter.
> I followed just about every how-to on the net, yet the only one that would boot via the instructions was the [**PendriveLinux** ]("http://www.pendrivelinux.com/")flavor, all well and good, but I really wanted either 9.04 or the 9.10 flavored **[Ubuntu-Gnome]("http://ubuntu.com/")** to boot as an install medium for clients machines, as well as a troubleshooting tool.

To make a very long story short, I laid finally ended up formatting a "fat16" partition on the "1st" 4gb of this 16gb drive(the rest whatever layout ya need to use), then ran [COLOR=Red]**[Unetbootin]("http://unetbootin.sourceforge.net/")**[/COLOR] to install the given( in this case, 9.10alpha .iso)and bam!, Houston, we now have a drive that boots!

Finally, and _just about every how-to I ran across on the net states to format the partition as fat32_. Well not in this case mission control, [COLOR=Red]_it's fat16_[/COLOR]

**Note:**
For anyone running across a drive with [COLOR=Red]_the miserable "U3"_[/COLOR] , it lies on as an "isofs" boot partition, and MUST be removed. Just go to the sansdisk site and download the windoze-only tool named the [COLOR=Red]**[U3 Launchpad Removal Tool]("http://u3.sandisk.com/launchpadremoval.htm")**[/COLOR] that will allow you to wipe all the partitioning off that thumb-drive your trying to get to boot. The thumb-drive WiLL NOT boot until this tool-wiper is run, period.[http://ubuntuforums.org/showthread.php?t=1273928](http://ubuntuforums.org/showthread.php?t=1273928)

---

### Post by bigboy_pdb on 2009-10-05
Based on the error, it appears as though your hard drive is still mounted when the program attempts to make the file system. Just try unmounting it before running the program.

---

