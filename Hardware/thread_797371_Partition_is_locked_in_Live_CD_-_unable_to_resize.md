---
title: "Partition is locked in Live CD - unable to resize"
date: 2008-05-17
forum: Hardware
---

### Post by Stason on 2008-05-17
I am running 7.10 on fake RAID

Here is what my partitions look like:

[---ntfs---]{---extended[ntfs]---}[-swap-][-ext3-][unallocated]

I want to increase ext3 to occupy the unallocated space. 

Booting from liveCD and running gparted I get this error:

====== 
Filesystem mounted or opened exclusively by another program?
e2fsck: Device or resource buzy while trying to open /dev/mapper/....
====== 

The partition itself has some error shown in gparted, which however never affected its functionality: "bad magic number in super-block, couldn't find valid filesystem super-block"

I am quite exhausted now, since I tried several ways and a couple of programs to deal with this, but still cannot increase my ext3 size. At this time I see the only sure way to solve this - is to reinstall Ubuntu completely, which, given the amount of time needed to configure it properly for my needs - basically means that I will be back to XP instead.

Any fresh directions would be greatly appreciated.

---

### Post by teaker1s on 2008-05-17
if your resizing ntfs and it wont play
run windows defrag
then```
 chkdsk /f
``` then reboot windows allow it to check disk and then you can repartition

possibly if as I under stand right that this is linux partition then fix super block by
[http://ubuntuforums.org/showthread.php?t=532735]("http://ubuntuforums.org/showthread.php?t=532735")
or you will need 
fsck -n /dev/sda1

this will not alter anything but report back errors on the file system.

Read/understand the errors and fix them

remember to fsck a partition not a disk

also

I don't know if this will help but on the GParted Live CD there is a very useful program called Testdisk.

Open a terminal and type Testdisk.

---

### Post by housam on 2008-05-17
You can resize your partition either by unmounting  the ext3 partition or using  the Gparted live CD: [[COLOR="Red"]_http://gparted.sourceforge.net/livecd.php_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Stason on 2008-05-19
> **housam said:**
> You can resize your partition either by unmounting  the ext3 partition or using  the Gparted live CD: [[COLOR="Red"]_http://gparted.sourceforge.net/livecd.php_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

My ext3 is not mounted since I boot from the livecd and I cannot use gparted liveCd, because it does not support fake raids.

---

### Post by Stason on 2008-05-19
> **teaker1s said:**
> 
or you will need 
fsck -n /dev/sda1

this will not alter anything but report back errors on the file system.

Read/understand the errors and fix them



run it from livecd - got "clean" report and yet in normal boot mode it gives lots of errors

---

### Post by Stason on 2008-05-19
> **teaker1s said:**
> 
possibly if as I under stand right that this is linux partition then fix super block by
[http://ubuntuforums.org/showthread.php?t=532735]("http://ubuntuforums.org/showthread.php?t=532735")


Tried that resize2fs -p trick - got something "everything is already fine" report.

Any more suggestions please.

---

### Post by Stason on 2008-05-20
Here is how it looks (ignore the lock signs - they are not there if I boot from livecd).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=70918&stc=1&d=1211319629[/IMG]

So how do I add that unallocated space to ext3?

---

