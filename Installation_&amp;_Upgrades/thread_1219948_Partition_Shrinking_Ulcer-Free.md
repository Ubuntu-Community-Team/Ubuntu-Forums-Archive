---
title: "Partition Shrinking Ulcer-Free?"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by ChristianMartel on 2009-07-22
1) This thread was initially submitted to: [http://forums.techguy.org/unix-linux/843883-ubuntu-choked-hangs.html#post6821769](http://forums.techguy.org/unix-linux/843883-ubuntu-choked-hangs.html#post6821769)   but more knowledge was req'd to answer.

2) Have submitted a request to Gparted team but such people tend to be very, very busy and may not have time for such inquiries, and I need to get this resolved as quickly as possible.


3) Here is the important and critical issue:

Have initially tried Ubuntu 8.04 installed in Win on NTFS partition.  Worked fine till I "choked" the small 10GB pseudo partition I created by adding an adding packages.

Decided to move to 9.04 on a seperate Ext3 partition.  **_I didn't go this route initially because I was concerned that when resizing the NTFS partition, I might accidentally squash the tail end of something on that partition. _**
 
When you Defrag a hard disk I don't know how to obtain the largest continguous space available, and if the partition manager, like Gpart, **does any checks when executing a resizing (downsizing) request**.

Here is the output of Fdisk and Du commands:
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10531    84590226    7  HPFS/NTFS
/dev/sda2           10533       12030    12032685    c  W95 FAT32 (LBA)
/dev/sda3           12031       12161     1052257+  d7  Unknown
 
 
ubuntu@ubuntu:/media/Nomade$ sudo du -s
37540483    .
 
 
But more importantly here are some screen shots of the issue:
 
[LIST=1]
[*]Gparted screen shot#1: overview of the hard disk situation on this HP Pavillion dv9000 notebook computer - indications that there are a bit more than 44GB of space to create a partition for Ubuntu; and in fact as can be seen in screen shots #2 & #3 this is confirmed - Gparted is willing to allow a reduction of the Win XP partition by about 45GB.
[*]Screen shot #4 is a map produced by the Win XP defrag program. This is after "defragging the hell out of the disk" as posted on another Ubuntu support item. The first issues appear:
[LIST]
[*]a significant amount of "unmovable" data is shoen
[*]a sliver of data at the end of the disk, presumably in the zone that would be freed after a Win XP partition reduction: thus resulting in loss of this data
[/LIST]
 
[*]Screen shot #5 is a similar map but produced with a defrag program by PerfectDisk (30$). This confirms concerns and brings a MUCH more important one: metadata such as boot records, file tables, etc. are NOT moved up to make space for a partition reduction.
[/LIST]
>>> Two other pertinent screen shots in following reply (max of 5 uploads per message).
 
So this would SEEM to explain why many people who want to go with a dual boot end up trashing their Windows system:
 
[LIST=1]
[*]It is not clear that the defrag process is an iterative one for most programs of this type
[*]Most defrag programs do NOT defrag and move metadata or "unmovable" data
[*]the partition program Gparted (or probably all others) does not seem to have enough checks and balances to avoid loosing critical metadata.
[*]simple methods of calculating available space do not provide checks and balances for not overruning a residually framented space
[/LIST]
So what I would like to know is how can I make sure that no metadata or other files that are to remain in the Windows partion will not be lost when I reduce that partition to make room for Ubuntu. Please see next reply for one last piece of info.
 
Thx  
 
xian

---

### Post by ChristianMartel on 2009-07-22
Two last screen shots:
 
[LIST=1]
[*]PerfectDisk screen shot#6: After consulting tech support at PerfectDisk they told me to use the "aggressive" mode to REALLY cleanup (defrag) my disk and maximize the available space. This involved online defrag, and offline defrag (i.e. at boot time before Windows comes online). WOW! as you can see from the screen shot the space is completely cleaned up:
[LIST=1]
[*]the "unmovable" data has been moved and consolidated
[*]a minimum breathing space has been intelligently left to Windows
[*]no meta data is left in the now large empty contiguous space
[/LIST]
[*]PerfectDisk screen shot#7: the machine has been rebooted and a couple of e-mails received as MS Outlook Express was still in the automatic start sequence during Windows reboot. So what drives me up the wall is:
[LIST=1]
[*]new files have been placed in the nice "clean & empty" continguous space in place of the Windows "breathing space"; but this can be cleaned again.
[*]a new boot sector(s?) has appeared; now if the e-mail is deactivated so no new data is written to disk, what is causing new boot sectors from appearing? If these new boot sectors are written by some automatic Windows process just before I reduce the partition size will I scrap my Windows partiton???
[/LIST]
[/LIST]
Would this be the driving force for the ever increase in popularity of WUbI and Portable Ubuntu version? That it is very hard to safely/reliably reduce the Windows partition?
 
Looking for insight and appreciating your patience,

Thx

xian

---

### Post by Mka on 2009-07-22
I've always used gparted to resize NTFS so as to open up some space for ubuntu. One of your attachments that shows the fragmantation analysis reveals that your Windows partition is not that much fragmented. I've resized NTFS partitions that are way worse than that with "unmovable" files all over the place without a problem.

One question I'd like to ask is: did you try to to resize the Windows partition and were unable to boot windows later on? or lost some data on windows? If GParted tells me it succeeded resizing, I treat that with confidence.

Also remember that windows defragments its filesystem while it is mounted. In linux, there are "immutable" files and cannot be moved, edited, nor deleted even by the root unless this attribute is disabled. But GParted can move the file when resizing because it operates at a lower level that normal copying, removal and deletion of files.

---

### Post by ChristianMartel on 2009-07-22
Hi Mka,

Yes as you can see in Screen Shot#6 the NTFS partion looks completly cleaned up, but then in Screen Shot#7 somehow a boot sector appeared after restarting the machine, which gave me cause for serious concern.

How many machines have you worked like this without a problem?  How many were Win XP?

Thx


xian

---

### Post by Mka on 2009-07-24
I have done this on many machines over the years from since NTFS support to linux was read-only only (remember the Hoary days?). If you are too paranoid identify and copy those so-called unmovable files to an external USB flash disk, for example, and go ahead with resizing you partition. If Windows cries because these files are missing or corrupted, use the ubuntu live cd and mount the windows partition and "inject" these files back into that partition.

---

