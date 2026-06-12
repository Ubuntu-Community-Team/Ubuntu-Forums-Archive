---
title: "Install Problem - No Partitions on existing Windows system"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by TheLastRaven on 2009-09-15
Apologies if this is answered elsewhere, I searched and didn't see anything on it, though. I also apologize if any of my terminology (I know Windows pretty well, but not so much on file systems) is off, as I am posting this from work, and the notes I had taken are sitting on my desk at home.
 
I finally decided to switch to give Ubuntu a shot and try a dual-boot (Ubuntu 9.04/Win XP) setup.  My plan was to run 3 logical partitions for Ubuntu and another primary partition as FAT32 to share data between OSes.
 
I am running a Sony Vaio (that I am kicking myself for buying some days) running Windows XP Media Center Edition.  I have 124GB of 291GB free on C: (my only HD), according to Windows.  However, when I "Manage" my drive, it shows an unlabelled volume of 7GB as a Primary Partition, followed by volume C: as a 291GB Primary Partition.  
 
Now the Problem: When I try to run my Ubuntu installer, from the CD as directed, the partition manager comes up and says there is no operating system on the hard disk, and lists ssda\ as SCSI1 160GB HD and ssdb\ as SCSI2 160GB HD. These are listed as all free space.  I considered wiping the drive out completely, but I have no idea where my Key is to re-install XP, and I still want to run XP because my printer and scanner are incompatible and my wife is unwilling to touch the computer without Windows at this point.  
 
Does anyone have any ideas on why the partition manager isn't seeing any existing OS/partitions? Any suggestions or pointers on where to go from here?
 
Any advice is much appreciated, I hope to be up and running Ubuntu soon!

---

### Post by Bartender on 2009-09-15
First off, don't delete Windows if your wife wants it on there!  It's not worth it.

The 7GB primary is probably the Media Center stuff.  Seems that most Media Center PC's have an extra partition.

Are you sure those are the only two partitions?  There's no recovery partition?

And you're absolutely sure there is one HDD?  I don't remember ever reading a thread where someone was having a problem with the Ubuntu CD identifying one drive as two.  Did Ubuntu actually describe them as ssda & ssdb, not sda & sdb?  Cause I've never seen that either.

Do you have recovery discs, or did you make them at some point in time?  You can find out your Windows COA key by downloading Belarc (a small download) then running it.  Belarc will report the Windows COA.

---

### Post by TheLastRaven on 2009-09-16
Bartender,
Those are the only two partitions that I know of, I don't know any other way of checking.  I am not absolutely sure that there is only 1 HDD without opening the case, is it possible that there are physically two 160GB drives that read in windows as a single 298GB drive? 
 
I will have to double check, but I think maybe they did report as sda and sdb, like I said, I have the info written down elsewhere.
 
I have a recovery disc that I made recently.  I couldn't tell you for sure if the computer ever came with one or not, it was about 4 years and two moves ago.  I will use Belarc, though, to retrieve the COA.  Hopefully I can get away without having to use a recovery disc, because I don't have much faith in them, but I definitely need the back-up plan.
 
Also, if it is of any help, I did a disk cleanup and skipped the defrag before my first install attempt, defrag only reported 1% fragmentation.  After the first install attempt failed, I defragged (Windows now reports only 3 fragments in the entire file system) and also tried a chkdsk /f which fixed one bad sector. After all of that, I still had the same problem...so I suspect the hard drive(s) is/are good.  Will verify the descriptions and see about looking at the device manager for HDD info and add that info back later.

---

### Post by TheLastRaven on 2009-09-16
Ok, I did double check, and the Ubuntu partition manager is registering sda and sdb. I only see the two partitions of 7 GB and 291 GB (C:\)...
 
I was just doing some more research, and was wondering if having not used a Gparted disc first is causing my problems.  Any chance trying a Gparted LiveCD and then trying the installer will prove more fruitful?
 
Any ideas?

---

### Post by TheLastRaven on 2009-09-17
Ok, last of the info I have:
 
The 7GB partition looks like the recovery partition, it is labeled in Windows as (Healthy) EISA Configuration. Looking at the device manager, I only see one physical drive...short of tearing the case open to look, that is the best I know.  Anyone have any suggestions??

---

### Post by wilee-nilee on 2009-09-17
Here is a great open source key finder free, every body should know about this.
 
[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)

---

### Post by TheLastRaven on 2009-09-25
Anyone else had similar problems?  Any suggestions as far as the partitions go?

---

