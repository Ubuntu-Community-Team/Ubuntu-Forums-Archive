---
title: "new system drive configuration recommendations"
date: 2008-09-09
forum: General Help
---

### Post by hwttdz on 2008-09-09
First let me apologize if this is way in the wrong place. If you can recommend a more appropriate forum to post this please let me know.  

I am looking for advice as far as hardware and raid configurations. In a perfect world I would have my data seamlessly accessible from both windows and linux, and the hard disks would be blazing fast.  

So far the best approach I can come up with is 5 disks:
1 & 2 -> raid 1, called disk A
3 & 4 -> raid 1, called disk B
5, no raid (probably a velociraptor drive, for low seek time, random reads, although I just had a raptor fail after 1.5 years so I'm hesitant on this front)

Disk A would be partitioned and hold my operating systems.  Disk B would hold my data (i.e. /home and windows username directory, set to the same location if possible, I know that's unlikely because ntfs doesn't play well).  And finally disk 5 would be a swap and page file disk.  ([howto]("http://tldp.org/HOWTO/Swap-Space.html#toc6")). 

My questions are:
1) do I get much performance benefit from having the swap space/page file on a different physical disk than the os?
2) the same for the os and the data?
3) Are there any alternatives you can think of that are redundant, allow data access from either partition, and hopefully are fast?  I'm trying to limit the number of drives as 5 seems excessive already.  If you can think of something on 5 drives that would be faster or fewer drives that would be equally fast I would be thrilled. 
4) Would raid 0+1 and turning 4 disks into one, and splitting that into 4 partitions be faster? 

Unnecessary background:  I ask this after having my current OS drive fail.

---

### Post by bingoUV on 2008-09-09
Do you have a hardware raid controller, or you hope to use software raid? I don't know of any method where windows and linux can read from the same software raid system. But then, I don't know much about windows.

1. You may get no performance benefit by having different drives for OS and swap. This is because with RAM so cheap, there are few systems indeed that use swap at all. If you are using swap, even a raid 0 with 10 drives will not help you in performance. Sell a hard disk and get a stick of RAM which alleviates the need to swap at all.
   Similar should hold for windows page file, but I don't know much about windows.


2. Different drives for os and data: Practically, not much of a speed-up is visible. Having both os and data on the same raid0/raid1 system has more of a benefit.

---

### Post by hwttdz on 2008-09-09
I have an ASUS p5n32 sli premium motherboard, which according to the manufacturer:

NVIDIA nForce® 590 SLI&#8482; chipsets incorporate six Serial ATA connectors with high performance RAID functions in RAID 0, 1, 0+1, 5 and JBOD.

So I could do hardware raid there, correct?

I have more than sufficient memory 3G, so I'll buy that system speed is not overly dependent on swap or page speed.  

So you would suggest a raid 0+1 configuration, where the amount of space that I have is equal to the twice the size of a single drive of which I need 4?

---

### Post by dannyboy79 on 2008-09-09
i opened this thread to help but I don't know much about raid but I can tell you something about having OS (programs) and data on seperate hard drives. I run MythTV which uses a MySQL database, I have that on my / partition (1 hard drive) and where the recordings are stored is on another hard drive and it does make a difference. MythTV does a lot of sql querying (or what have you) in the background when using MythTV so it's beneficial to have your recordings stored on another drive. Just my 2 cents......

---

### Post by listener on 2008-09-09
Are you sure that is hardware RAID?  I have a 570 chipset which sounds like the same RAID, it is not recognized as an array in Ubuntu, but as individual drives, under RAID 1.

I'm not entirely familiar with any difference between the chipsets, but I suspect it is exactly the same RAID.

I have a RAID 5 four-drive max (three or four drives in RAID 5) completely hardware card (has cpu onboard) and assuming it is properly recognized by Linux, if you are determined to use RAID, I'd recommend RAID 5 (or even 6) with that many drives.  It gives a performance boost and data protection. 

I've tried lots of RAID systems however, in attempts to protect data, and invariably wind up losing it due to the RAID controllers.  It takes a lot of $$ for a really reliable RAID system.  The controller I mentioned was $400 and was inexpensive at that.  I'll say it was a good one until it dropped a drive however.

best

---

### Post by hwttdz on 2008-09-09
No in fact I'm not at all sure that's hardware raid, I merely assumed that the naming scheme was reasonable and because it was taken care of at the hardware level that it would be called such.  I would tend to agree with you that they are likely the same.  

I've seen some data which shows that raid 5 actually performs far worse than a bunch of single disks in some situations (not pathological).  

It seems I'm going to have to back up all my data (again) and nuke my computer entirely in trying to do this.  

It seems I've now gotten 3 different opinions in 3 different posts.  I think I'm every bit as confused as when I started.  And also it seems that the whole dual boot thing is made more difficult by raid.  Evil skype, and lack of support in 64 bit linux, and just poor open office calc not even coming close to excel.  

Thank you all for your opinions and information though. I know it's not an easy question.

Also if one is running raid 1, how do you know if a drive has failed?

---

### Post by bingoUV on 2008-09-10
> **hwttdz said:**
> I have an ASUS p5n32 sli premium motherboard, which according to the manufacturer:

NVIDIA nForce® 590 SLI™ chipsets incorporate six Serial ATA connectors with high performance RAID functions in RAID 0, 1, 0+1, 5 and JBOD.

So I could do hardware raid there, correct?

I have more than sufficient memory 3G, so I'll buy that system speed is not overly dependent on swap or page speed.  

So you would suggest a raid 0+1 configuration, where the amount of space that I have is equal to the twice the size of a single drive of which I need 4?

As far as my question goes, it will be called hardware raid. But on-board raid on consumer end motherboards does not give you much flexibility. I would be surprised if it let you create TWO raid-1 arrays from 4 drives. Try reading the manual and figure out if it is possible.

With 3GB memory, you may not hit swap at all. So it wouldn't matter if swap is in a different drive than the OS. As dannyboy79 suggested, if some part of your filesystem is likely to get heavy hard drive usage (like MythTV) it would be better to separate it out on a separate filesystem and separate hard drive.

0+1 maybe good but remember raid is not for data protection. It is only for uptime i.e. a drive crash does not stop your system from working. If through software bug/user error you delete your important data, raid will not help you. You need backups for that.

EDIT: some kinds of raid help performance too, of course.

---

### Post by listener on 2008-09-10
I looked around, there may be ways to get this to work with Ubuntu, but it looks like it may be a pain (the 590 chipset RAID).  It takes an OS driver.  I did not read extensively, but it looks like there are a lot of problems.  I know mine appeared as individual drives.  Also, whether a controller has its own processor or not, is one thing... may not be important.  In this case, it goes a step further, as the RAID function depends on (OS-based) software.  A good way to think of it, possibly, is the problems a few years ago with 'soft modems' or 'winmodems'.  They usually had no support in Linux, as they depended on software to work.

If RAID 1 fails while in Windows, provided you have the Windows software which monitors it installed (comes with the RAID controller no matter what kind) it will inform you, in two or three possible ways.  Probably at home, you'd simply have a visual and audible alarm.  You can usually have an email sent, if monitoring a remote system.  You can have a spare drive right on the system to automatically recover if it is important enough.
If not handled by software in the OS, the controller bios will alert you at next reboot, probably halting the boot. I do believe my Areca card came with Linux software, as cards like that are used in servers, etc.

RAID 5 on a 'real' controller speeds things up quite a bit, although I don't recall the benchmarking I had.  Very noticeable.  I saw in one of the articles on the nForce RAID that yes, it is slow, if you do try to use that one.

If I wanted a lot of speed for the drives (having nothing to do with separating data from system) I personally would try a Raptor or maybe more than one, but not in RAID.  This is my opinion though, however based on a lot of experience with RAID.

All that said, I don't know much at all about it, but Ubuntu provides it's own software RAID, which is called dmraid.  

You really have more than one question, whether to separate OS from data, and whether to use RAID.  They are very much different questions.

Hope that helps some.

Edit: should have said: I agree very much that more RAM is the best way to speed things.

---

