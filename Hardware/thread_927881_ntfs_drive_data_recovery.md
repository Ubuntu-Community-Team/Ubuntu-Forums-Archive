---
title: "ntfs drive data recovery"
date: 2008-09-23
forum: Hardware
---

### Post by Pacifik on 2008-09-23
I have two hard disk (Seagate SATA). In the first hard disk Win XP is installed, having 4 NTFS partitions. In second Ubuntu 8.04 is installed. All of a sudden, NTFS volume doesn't mount in Ubuntu. When tried to mount it, gives error: *NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE.* 

Then I tried to boot into XP, but couldn't boot. It just hangs. I cannot format all the NTFS drives. I have important documents in 3 drives (partitions other than XP installed). I formated the drive where XP is installed from Ubuntu. Then I tried to install XP. Here I had messed up something (couldn't remember).

When booted from Ubuntu and tried to run *#fdisk -l* command, it did not showed the first hard disk. The partition table may be corrupt, or so. 

I have removed the first disk. Now MBR is in the second hard disk, and running Ubuntu fine. Now I wanted to recover the important datas in the three partitions (NTFS) in the first hard disk.

Your help will be highly appreciated.

---

### Post by Pacifik on 2008-09-24
Please help me out...........

Will **testdisk** software help in my situation ?

---

### Post by DrMelon on 2008-09-24
It seems you have encountered hard drive failure. Data recovery programs and tools can help, but there doesn't seem to be much I can think of. Somebody else probably has better ideas, but I suggest taking it to the manufacturer if it's in warranty. If not, you may have to pay to get somebody to take the data off of the platters.

---

### Post by seeker5528 on 2008-09-24
Testdisk is definitely worth a shot.

I normally keep a current version of [System Rescue CD]( http://www.sysresccd.org/Main_Page) around because it stays pretty current with the NTFS tools and testdisk stuff.

For the last few releases testdisk has had the file copy capability with NTFS, after you do the inital scan, then do the deeps scan, it has the option to choose a partition and list the files, when the files are listed you have the option to copy them to another partition. You don't want to do any options that will write changes to the drive you are recovering from until you verify the copies of the files you need to save are good.

There are some examples of use [here](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS) and [here](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

The copy feature is relatively new and I have not had the opportunity to test it in a file recovery type situation.

If that fails then the other DIY options I have had good results with are designed to run from a windows installation, and cost money, but you can download them and check them out first.

The first of these is [Get data back](http://www.runtime.org/), in the trial version as long as you have the software installed to handle the files you want to recover you can open up as many files as you want to see if they look OK. 

The second one is [Easy Recovery Professional](http://www.ontrackdatarecovery.com/data-recovery-downloads/). I have only used the full program, not the trial, and the web site indicates the trial only allows you to recover a single file, so I don't know how useful that really is as an indication if it will work for you. I have had it work for me in situations where Get Data Back failed, but I fully expect in some situations the reverse would also prove to be true.

Later, Seeker

---

### Post by Pacifik on 2008-09-24
I will be downloading the "System Rescue CD" and try with **testdisk** software first. Hoping it to work.

Meanwhile, today when I booted into Ubuntu system and done "sudo fdisk -l", I could find my first hard disk listed with NTFS filesystem mentioned. This is strange to me. As yesterday I couldn't find the same list. I think, this gives the sympton that the partition table of first hard disk is not damaged. Am I right?

---

### Post by seeker5528 on 2008-09-25
If fdisk sees it, that doesn't mean it's not messed up, but it could be a good sign.

Still leaves the question of why it didn't show up, then showed up again.

Most problems with the drive would be caught by, [SeaTools](http://www.seagate.com/www/en-us/support/downloads/seatools/), but some intermittent problems where the drive just stops working, then starts, then stops, then starts may not get logged in the smart record.

If the drive is exhibiting behavior where it just stops working, doesn't show up any more, then you unplug the drive, set it aside for a day, plug it back in and it shows up for a while, then stops again. If you can see the data using normal methods while the drive is operational, it is best to just grab what you can while it is working, in the hope that you will have long enough periods of operation to get what you need off the drive. The longer it operates that way, the more likely it will quit completely so in that specific type of situation spending the time using something that has to do a lengthy analysis of the drive before you can get any data off is not so desirable. 

Reason being the length of time it takes to do the analysis may be shorter than the amount of time you have to work with the drive before you have to set it aside for another rest period, and/or be long enough to make the difference between getting all the data off, only some, or none. 

I have seen drives stop working, come back briefly after setting them aside for a while, then give up the ghost, with no prior warning, and not much time to get data off the drive. I've seen others that stop working after 2 or 3 hours, set them aside or unplug the computer from the power for a while, then they go for another 2 or 3 hours, and so on, but you get time to get the data off the drive.

Seagate is pretty good about replacing drives that are under warranty, but don't know what they are willing to do in relation to the data, and sending it to a lab is expensive, at least relative to my budget.

Later, Seeker

---

### Post by Pacifik on 2008-09-25
Please look below post.

---

### Post by Pacifik on 2008-09-25
In Ubuntu system when the first hard disk (the problematic one) was recognizing, I tried to mount the partitions. But failed to mount. Then tried to recover the datas using **testdisk**. The system was just freezing. When tried to shutdown the system, it was not halting. I have to forced the system to shutdown. Again booted, again the hard disk was recognizing.

That was the last time I could see the problematic hard disk. I tried to use "rescue cd", but the hard disk was not recognizing. The BIOS also was not recognizing the hard disk. 

But the interesting part is: when the two hard disk is connected, BIOS and operating system couldn't detected either of the hard disk (but previously it was detecting both). When using only the second one, all was fine.

What may be the problem?

The hard disk is **Seagate BARRACUDA drive S ATA**, and is in warranty period.

---

### Post by seeker5528 on 2008-09-25
If one drive is failing it can cause all the drives not to be recognized, but having each get recognized individually, and neither when they are both hooked up is a bit odd.

I would check the bois for any raid related options, sometimes it's an integrated function where you can choose raid more ir ide mode, sometimes raid is a separate function that you choose to disable if you want the drives to work individually.

If it is an option I would also try the drive that is having issues in another computer to see how it acts there.

Also if you can get one of [these](http://www.xpcgear.com/usbdsc5.html) types of adaptors, you might be able to get around the issue by hooking the the problem drive up internally and the other one externally.

Later, Seeker

---

### Post by Pacifik on 2008-09-25
I will check the drive in some other system, shortly.

---

### Post by Pacifik on 2008-09-27
I have checked in other system. And seeked help with a hardware expert. The hard drive has failed, and have to replace it. Thanks God that it is in warranty period. Only issue is that the datas are gone. Its a great learning for me - **always take backups regularly**.

When the hard disk was connected to system, it was not detecting. No entry in BIOS. And the hard disk was making sound, like *cut - cut - cut ...*.

Anyway, thanks guys for all your co-operation and great community. Ubuntu community is really great - for novice and expert.

I am using Ubuntu since 1 yr. And found that it is one of the best OS - because of its user friendliness, APT, and great community. Linux has come a long way and is really excellent. Only major issue is many proprietary softwares/apps are not made for linux. Hopefully, within a few years this scenario will change.

bye.

---

