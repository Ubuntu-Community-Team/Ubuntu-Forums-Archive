---
title: "Data Recovery Questions..."
date: 2011-03-06
forum: Hardware
---

### Post by Xswitch on 2011-03-06
Got Grub Error 17...  80 Gig Seagate HDD for a Laptop.  /, /swap, /home  ...  System will not boot.  Will not boot with Live CD either...  

1. Ran BIOS Diagnostic to test HDD...  got error reading drive...

2. Put HDD in Enclosure and plugged in to another Ubuntu system... Does not show up...

I believe the HDD has failed, but need to recover info...

**QUESTIONS:**
1. Is it possible to have the drive imaged, so that when I get the new drive, I can just plug it into my laptop as if nothing ever happened?

2. **[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)** states that it is advisable to image the device and then work on the image to recover data.  Is it safe to do this on a damaged device?  Am I making things worse by attempting to image?

I'm not sure that even an attempt at imaging would work, due to the fact that I can not get the HDD to "show up" on any system...

Thanks all...

---

### Post by Telengard C64 on 2011-03-06
:(

It sounds like your hard disk is permanently damaged. Depending on the nature of the damage, you may do more harm than good by trying to use it for anything.

Are the platters even spinning up?

I don't know if there is much you can do for yourself here. (Maybe someone else will have some ideas?) A professional data recovery service could certainly recover your data. They can extract the platters and read them from their own specialized equipment. It will cost $$$.

The best way to recover your data in this situation is **from backups**. I don't mean to be insensitive, but this kind of situation is exactly why people harp on the need for a reliable backup strategy.

RAID 1 could have saved saved you here. Assuming only the hard disk itself failed (not the motherboard), the data would still be living happily on the twin drive.

Sorry to be so pessimistic about your odds of getting things back. That's the best advice I can come up with given the circumstances you describe.

I wish you much luck.

---

### Post by Xswitch on 2011-03-07
Thanks Telengard C64...  You know, I just kept putting it off and just kept delaying my backup strategy ...  and now this... :(  I need my data, so it looks like I'll have to hire a professional...  Not sure the drive is even spinning up...

EVERYTHING CHANGED FOR ME THIS PAST FRIDAY!!!  Here's what I'm doing going forward.

1. Purchasing a new Laptop from PowerNotebooks.com  (THIS IS LONG OVERDUE ... getting the best they have to offer)

2. Hiring a Professional Data Recovery service to retrieve my data.

3. IMMEDIATELY INSTITUTING THE BEST BACKUP SYSTEM THAT MY MONEY CAN BUY OR THAT I CAN FIND!!!  I NOW HAVE **ZERO** TOLERANCE FOR DATA LOSS / HDD CRASHES, ETC...!!!

This will no doubt make me much "lighter in the pocket" but **I AM VOWING TO NEVER BE IN THIS SITUATION AGAIN...  EVER!!!**  Money may not be able to buy love, but it can sure buy just about everything else... :lolflag:

Thanks for letting me vent a little... :P   I'm totally pissed at myself... 

It is indeed a new day for me...  I guess it took something like this for me to wake the heck up!!! I'll be back though...  THIS TIME WITH A BACKUP SYSTEM 2ND TO NONE!!!

---

### Post by apernix on 2011-03-07
i've heared there are method to recovery data from damaged harddisk by put it on refrigerator like at [this articel]("http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html"). But there is still no warranty that your data will back 100%, but it still worth a try i think. :)

---

### Post by Xswitch on 2011-03-07
Thanks apernix, but this puppy is going into the hands of a professional... I AM TOTALLY OVER IT!!!  Money right now IS NO OBJECT!!!  :P  ...  I totally screwed up this time, but now I'm going to fix it with CASH!!!  This pretty much sucks, but I knew better...  And I have no one to blame but myself... #-o](*,)

---

### Post by Telengard C64 on 2011-03-07
> **Xswitch said:**
> 3. IMMEDIATELY INSTITUTING THE BEST BACKUP SYSTEM THAT MY MONEY CAN BUY OR THAT I CAN FIND!!!  I NOW HAVE **ZERO** TOLERANCE FOR DATA LOSS / HDD CRASHES, ETC...!!! I'll be back though...  THIS TIME WITH A BACKUP SYSTEM 2ND TO NONE!!!

That's the spirit!  :D

Seriously though, external HDDs and small NAS boxes are quite affordable now. Just to give you something to compare with, study the feature set on these. I'm not saying to buy them, just look at the features:
[http://buffalotech.com/comparison-charts/network-storage/home-and-small-office/](http://buffalotech.com/comparison-charts/network-storage/home-and-small-office/)

You get some crappy backup software for Windows, A few features which only apply to Apple products. But you also get, FTP, web, RAID, etc.

Just in case you don't know what RAID is and how it *protects* your backups with *redundancy*:
[http://raid.com/04_00.html](http://raid.com/04_00.html)

**IMPORTANT NOTE**
RAID is *not* a backup strategy by itself. A proper backup strategy uses external media and offers the possibility of multiple generations of data recovery. RAID does not do either of those things. The one thing RAID can do is *protect against hard disk failure*. Read the tutorial linked above to learn how!

A backup strategy can be a simple or complex as you make it. Here are somethings to think about.

[list]
[*]What data to backup? Full hard disk, or just /homes, or a combination of both?
[*]How often to backup? Daily? Weekly? Monthly?
[*]Should multiple backups be kept? Is it important to have access to your data as it was last week, last month, and last year? How many generations of backups?
[/list]

A lot of people would recommend doing full disk backups periodically. That's a fine idea, but it is slow and the software has some peculiarities you need to study. For example, what if your backup can only be restored to exactly the same size disk?

 A better idea would be to backup only /home plus any other important data you have in different folders. There's no need to include all 20 Linux kernels and various libraries, and text documentation in your backups. 

If you just want cheap and quick, you can purchase a USB HDD. Then once per day/week copy your /home to it. After you've got that habit learned you can take some more time to ponder how to make your system faster, easier, more reliable.

---

### Post by oldfred on 2011-03-07
I tend to disagree on RAID as a backup. If you say delete all files then all data is deleted and it is no backup. Backups have to be to another device and should also be to a off site location. I use DVDs and only copy my data, not system. I figure I can reinstall Ubuntu from scratch in about an hour. My backups include installed programs, custom configs from /etc and my /home hidden settings as well as all my data. But my personal data is not as vital as a business or professionals needs, which may need to be daily or every more often.

Does BIOS see hard drive. If not then you have major drive problems. I have heard some recovery horror stories where users did not ask about cost and they spent thousands and all the service did was run testdisk.

---

### Post by Telengard C64 on 2011-03-07
> **oldfred said:**
> I tend to disagree on RAID as a backup. If you say delete all files then all data is deleted and it is no backup.

Please read what I wrote.
I never recommended RAID as a *backup*.
I recommended RAID to *protect* backups.
RAID can protect backups with *redundancy*.
Some people like redundancy for very important data.
I will append a note to my post so no one else is confused like you were.

> Backups have to be to another device and should also be to a off site location

I agree with that, and everything else you said.

---

### Post by Xswitch on 2011-03-07
> **oldfred said:**
> I tend to disagree on RAID as a backup. If you say delete all files then all data is deleted and it is no backup. Backups have to be to another device and should also be to a off site location. I use DVDs and only copy my data, not system. I figure I can reinstall Ubuntu from scratch in about an hour. My backups include installed programs, custom configs from /etc and my /home hidden settings as well as all my data. But my personal data is not as vital as a business or professionals needs, which may need to be daily or every more often.

Does BIOS see hard drive. If not then you have major drive problems. I have heard some recovery horror stories where users did not ask about cost and they spent thousands and all the service did was run testdisk.

When I open BIOS and do a HDD Self Test, I get this error:

**Error: Read Failure**

When I boot normal, I get this:

[B]GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17[/B]

**Here are a few concerns that I have...**

1. I have Virtual Box installed with Win XP in the Virtual Environment...  I have data stored in the VM.

2. I tried booting to a Live CD... Knoppix and Ubuntu... and the drive is not detected...  I tried with a HDD enclosure and plugging the HDD direct into the laptop.  Doesn't the drive have to "show up" in order to run testdisk?

3. Will testdisk further damage the drive?

Just ran a "Startup Check" via the BIOS...  This is what I got:

[B]Startup Check Failed

Status = Failed - Replace Hard Disk 1
Warranty ID = (A Whole Bunch of Numbers) :)[/B]

---

### Post by oldfred on 2011-03-07
If you are getting grub legacy's error 17 that is partition not found. It could just be a damaged partition table. If grub is booting that far then it at least starts to see the drive.

I would try testdisk from a liveCD. Test disk scans drive for any data that may be recoverable. It does not rely on partition table or the file info. It just looks across drive for something that looks like a file. But BIOS has to see drive. If grub starts to boot BIOS must see drive.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Xswitch on 2011-03-07
Thanks for the info Telengard C64...  All of my options are open on this one...  **I'M LEAVING NOTHING ON THE TABLE!!! **

---

### Post by Xswitch on 2011-03-07
> **oldfred said:**
> If you are getting grub legacy's error 17 that is partition not found. It could just be a damaged partition table. If grub is booting that far then it at least starts to see the drive.

I would try testdisk from a liveCD. Test disk scans drive for any data that may be recoverable. It does not rely on partition table or the file info. It just looks across drive for something that looks like a file. But BIOS has to see drive. If grub starts to boot BIOS must see drive.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

This is cool oldfred...  But I'm still concerned about the BIOS errors that I received....  I have a ?

**Do I install testdisk on another machine and then put the bad HDD in an enclosure and plug that into the good system?**

---

### Post by oldfred on 2011-03-07
If you can boot a liveCD you can do that. If testdisk works then you do not need other drives nor computers. But if it does not then you have to use photorec to recover files.

But tehn you do need to have another drive or USB key that is large enough for your data. 

Or you can plug it into another computer. What every seems to work best.

I used photorec which is part of testdisk to recover some missing data. For example I have saved some text files many times on a good sized drive. Photorec found every copy I had saved. Not sure if I ever found the last saved one as it does not recover names nor dates. But between backup & several of the versions I was able to recover most of that file. Lots of grepping & comparing. Not fun.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by Telengard C64 on 2011-03-07
> **oldfred said:**
> If you are getting grub legacy's error 17 that is partition not found. It could just be a damaged partition table. If grub is booting that far then it at least starts to see the drive.
...
If grub starts to boot BIOS must see drive.

I agree, this *is hopeful news*. If **grub** is starting up that means your drive is spinning up and at least part of the disk surface is readable. The drive mechanism may not be broken, but maybe there is some partition table damage or filesystem corruption.

You may indeed be able to recover data with **testdisk** and **photorec**. Proceed with all due caution as oldfred recommended.

---

### Post by Xswitch on 2011-03-07
Hmmm...  Interesting update... Just put HDD back inside my laptop and was able to boot using a Knoppix CD, but I was unable to boot using the Ubuntu CD.  Funny thing is, that I just used that CD to install Ubuntu on another machine, so I know that the Ubuntu CD is good..   Not sure why Knoppix worked and Ubuntu didn't..


oldfred, I did not see instructions for creating a Live CD with testdisk on it.  I did download testdisk on a Windows box and ran the .exe just to see what it looks like.  Can u tell me how to get testdisk on a CD to run on Ubuntu, or on a USB flash drive?

---

### Post by Xswitch on 2011-03-07
Think I found a Knoppix with testdisk...

---

### Post by oldfred on 2011-03-07
A lot of Linux repair liveCd have testdisk. 

Ubuntu has testdisk in the repository:

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Xswitch on 2011-03-07
Booted with Knoppix 6.4 ...  and ....  **I CAN SEE THEM!!!  I CAN SEE THEM!!!  I CAN SEEEEEEEEEEE THEEEEEEEMMMMMMMMMM!!!  **:lolflag:  

Drive shows as sda3.  I'm getting closer...  I THANK G-D FOR YOU PEOPLE...  

Gonna run testdisk...  I'll report back....  I pray this fixes my boot problem...

---

### Post by Telengard C64 on 2011-03-07
Now that you can see the files ...

**Back them up to an external drive, networked computer, optical disk, or flash media. Do this before anything else.**

---

### Post by Xswitch on 2011-03-07
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End     Size in sectors

No EXT2, JFS, Reiser, cramfs or XFS marker
 [B]1 * Linux                    0   1  1  1215 254 63    19534977
 1 * Linux                    0   1  1  1215 254 63    19534977[/B]
 2 P Linux Swap            1216   0  1  1823 254 63     9767520
 3 P Linux                 1824   0  1  9728 254 63   126993825

....

First Partition listed twice...  Site says the following:
The first partition is listed twice which points to a corrupted partition or an invalid partition table entry.

**I continued and then I got this:**
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63

The harddisk (80 GB / 74 GiB) seems too small! (< 101 GB / 94 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
   Partion                 Start        End    Size in sectors
HPFS - NTFS           9728 254 63 12377 144 21   42547324


[Continue]
NTFS, 21 GB / 20 GiB

?????

It also asked me about Vista???

---

### Post by Xswitch on 2011-03-07
I continued and got this:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9730 255 63

[B]Partition            Start        End     Size in sectors
* Linux Swap     1216  0  1  1823 254 63    9767520
P Linux          1824  0  1  9728 254 63  126993825[/B]

Looks like I'm totally missing **/** root

Here's what appears at the bottom of the screen:

Structure: Ok.  Use Up/Down Arrow keys toselect partition.
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A:  add partition,  L: load backup,  T: change type,
     Enter: to continue
**SWAP2 version 1, 5000 MB / 4769 MiB**  **{THIS SEEMS TO BE THE SIZE OF MY ORIG. /}**

Don't know and not sure what to do next...

---

### Post by oldfred on 2011-03-08
I have not used testdisk to recover a drive. But if it is not working or you want another way.

I would do this anyway.
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)
Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

---

### Post by Xswitch on 2011-03-08
Copying /home over to a 500GB drive...  Just did a drag and drop.  Here are some errors that I'm getting:

**Some errors occurred:**

**socket:** Can't copy special file
**Commands:** Can't copy special file
**Notification:** Can't copy special file
**.kde:** Permission denied

I'm at 80% copied...  This looks much better that yesterday... but I seem to be making some progress...

---

### Post by oldfred on 2011-03-08
If you were booted, a file or two in /home are always open and may cause errors. But since you had just mounted it to copy, it seems like a file or two have problems and may be related to the entire issue??

If you look in system, Admistration, Disk utility and click on the drive. What does it say about drive. I do not know how to understand Smart Data but it gives an overall rating.

---

### Post by Xswitch on 2011-03-08
Hey oldfred...  My drive is now in the hands of a professional. :P  I gave them **ALL** of the details of the situation...  I told them about the structure of the drive... I told them about my virtual machines (vbox)... etc... etc...  I gave them as much detail as possible about the situation...  My hope is that they will be able to just image the drive, that way I can just pop it into my laptop and boot.... 

I feel better, but still very anxious...  I'll let you know what happens...  **THIS WILL NEVER HAPPEN TO ME AGAIN!!!  I AM GOING TO MAKE SURE OF THAT!!!**

---

### Post by Vege 4wd on 2011-03-09
Great thread.

 I am jumping in here because I deleted my home file and am heading down this path.
I have been using test disk not with a live cd.

My question is how do you back the files up to another drive? I have a usb drive connected or is that option only available with one of the live cd's?

Test disk is running now and I am up to the part where I can start to search for particular file type. Maybe it will be apparent later but I am away from laptop for the day and need the files now. 

Thanks in advance.

---

### Post by Telengard C64 on 2011-03-09
> **Vege 4wd said:**
> Great thread.
My question is how do you back the files up to another drive?

If you have already deleted the files, and they are not in the trash bin, then it becomes much harder to backup the files.

First you must *immediately* cease all activity on the hard disk in question.If this is the same hard disk with your root or home directory on it then you should unplug the computer from the wall *without shutting down*.

Next you should make an image file from of the disk with, for example, **dd**. Because your deleted files no longer have links in the filesystem the disk blocks which contain them are considered *free*, so it must be a full disk image.

Now that your data is protected in a backup disk image you can use a tool like **photorec** to get the files copied to an external storage device.

---

### Post by Xswitch on 2011-03-10
> **Vege 4wd said:**
> Great thread.

 I am jumping in here because I deleted my home file and am heading down this path.
I have been using test disk not with a live cd.

My question is how do you back the files up to another drive? I have a usb drive connected or is that option only available with one of the live cd's?

Test disk is running now and I am up to the part where I can start to search for particular file type. Maybe it will be apparent later but I am away from laptop for the day and need the files now. 

Thanks in advance.

Thanks Vege 4wd ...  I was able to backup /home to a 500GB external using a Knoppix Live CD... 6.4...  My problem was that I had VBox running with Win XP as a Guest and had some very important files inside the VM...  I also use Moneydance for financials, and for the life of me, I do not know where the files are being saved....   Sooooooo...  Yesterday I got a call from the Data Recovery Co. that I'm using...  Looks like it going to cost me about $400.00 US.  

The new drive will be bootable...  Looks like they have to copy it sector by sector.  Bad sectors on the / partition... /home looks ok...  I'll let you know what happens next...  Should have new PC soon and still researching and planning my new STATE OF THE ART BACKUP AND RECOVERY SYSTEM(S) ....  I WILL NEVER, EVER BE IN THIS PREDICAMENT AGAIN...  Also investing in a Fire Safe!!!  I'm seriously not playing...

---

### Post by Telengard C64 on 2011-03-10
> **Xswitch said:**
> still researching and planning my new STATE OF THE ART BACKUP AND RECOVERY SYSTEM(S)

I'll be interested to read about it, whatever you decide on.

> Also investing in a Fire Safe!!!

LOL

What will go into it?

---

### Post by Xswitch on 2011-03-11
> **Telengard C64 said:**
> I'll be interested to read about it, whatever you decide on.



LOL

What will go into it?


LOL...  Hard Drives, of course... LOL...  Along with some Important Docs, photos, etc...  

Also, I decided on a RAID-1 setup with 2 1TB drives...

[B][U]So here's what I'm doing:
[/U][/B]
**Laptop from powernotebooks.com with 1 _90GB Solid State Drive_ and 1 500GB drive for storage...  I'll then backup to an External RAID-1 setup with 2 1TB Drives, preferably (Hotswapable).... **

This is the plan... :D

---

### Post by Xswitch on 2011-03-11
Also...  I forgot one critical thing that I'm going to do doing a lot of...

**EDUCATION...**

I realized that I really don't know what I should know about Linux and Ubuntu...  I also don't know much about Data Recovery...  I resolve to educate myself much more on both...  I am EXTREMELY interested now on the tools/Equipment used in the Data Recovery process...

---

### Post by Telengard C64 on 2011-03-11
> **Xswitch said:**
> **Laptop from powernotebooks.com with 1 _90GB Solid State Drive_ and 1 500GB drive for storage...  I'll then backup to an External RAID-1 setup with 2 1TB Drives, preferably (Hotswapable).... **

That sounds pretty good so far. A few questions might help me better appraise the effectiveness of your strategy. 

[list]
[*]What kind of backup (full disk image | compressed archives of files | simple file copy | other)?
[*]What software will you use to perform the backups?
[*]How often will you backup?
[*]How many generations of backups do you intend to keep?
[/list]

I'm really pleased to know you are taking this so seriously. I've lost data in the past, and reading stories like yours is a gut wrenching experience for me.

---

