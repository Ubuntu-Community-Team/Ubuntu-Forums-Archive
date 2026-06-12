---
title: "Data Recovery NIGHTMARE ... Desperately need help !!!"
date: 2010-11-17
forum: Hardware
---

### Post by WinRiddance on 2010-11-17
Geez, I can't even believe this is happening to me. It all started after my upgrade from Ubuntu 10.04 to 10.10 last Friday. Initially my external USB backup drive would no longer be recognized, refusing to let me mount the volume which worked fine in all other Ubuntu versions of the past 18 or so months. I spent days in this forum and on the internet without being able to remount that external USB drive ... probably due to my lack of knowledge/comprehension about the inner workings of Linux/Ubuntu. It's a non-bootable NTFS volume that I've been using strictly for data backup once per month.

Finally I gave up and decided to try data recovery instead, in order to retrieve my backed up files from the external drive that wouldn't let me mount it. **Using testdisk** I managed to find the right partitions with the data on the non-mountable usb drive ... but couldn't for the life of me figure out how to retrieve the data and copy it onto another partition on my primary hard disk. There are virtually no easy to understand, step by step instructions anywhere, for how to get that data to another location. Every time that I attempted to copy, testdisk tried to place the data in either home or my user location. I can't copy anything there though because there's only about 10 GB of space left on my system disk. That disk cannot be changed under any circumstances!

**It gets a lot worse though ....** :( :(

Finding out about ddrescue and reading up on it in the wiki while probably misunderstanding some of that information ... I then attempted to copy data directly from my non-mountable USB drive to another partition on my primary hard disk. I freed up all of the space that I could on my main data partition (Ubuntu system runs on a separate partition or I wouldn't even be here). Having 160 GB of space available, **I then installed gddrescue** followed by attempting to recover data FROM the usb drive TO that particular partition. I did neglect to create a folder in media, figuring since all of my data was within folders anyway that that would be alright as I'd be able to recognize the names of the copied folders later on.

Using this command:

**sudo ddrescue /dev/sdb1 /dev/sda3**

I tried to copy data _from_ sdb1 (the external usb drive) _to_ my sda3 partition with lots of free space (the one that I use for most of my current data files). Copying began and after roughly 15000 MB had been copied I decided to check on the sda3 disk with my computer file manager ... **[COLOR=DarkRed]only to find 0 files and 0 free space[/COLOR]** ... file system unknown ???

So now all of my backup data is inaccessible to me, with files (family pics, videos, emails, business letters, etc.) going back as far as 10 years ... and all of my primary working data from my sda3 partition is inaccessible too. To make matters worse (is that even possible), **using testdisk** on my primary data partition also shows 0 files and file system unknown, possibly damaged.

I am absolutely clueless what to do at this point. HEEEEEEELLLPP !!!!  :( :( :(

I have no access to Windows in order to use chkdsk /f on the usb drive and now I no longer have any other productive space on my primary hard disk in order to save or copy anything. I do have a working CDR/DVDR disk drive in my laptop though. I could probably reformat sda3 but that's the last thing I'd be receptive too as long as I don't have my backup data from the usb drive.

.

---

### Post by lukeiamyourfather on 2010-11-17
I've not used ddrescue but it probably copies one block at a time from disk to disk. So if you look in the destination you won't see files or folders until the process is complete. If there's no luck there I'd try checking the disk in a Windows system since the file system is NTFS. If that fails too then the disk itself might have failed.

---

### Post by WinRiddance on 2010-11-17
> **lukeiamyourfather said:**
> I've not used ddrescue but it probably copies one block at a time from disk to disk. So if you look in the destination you won't see files or folders until the process is complete. If there's no luck there I'd try checking the disk in a Windows system since the file system is NTFS. If that fails too then the disk itself might have failed.


Well, that may be, but since my backup drive was already inaccessible to me for data retrieval, I just panicked and stopped the copying process per ddrescue instructions, right there on the terminal screen. I would never have thought that this would happen. I've **contemplated doing a reboot or a cold start** but am terrified that everything might then be even worse ...
Besides, I only have access to a _WinVista_ system which won't permit me to use the **chkdsk /f** function on the backup drive. When I try that I receive a no can do message, due to missing permissions. No idea what that's all about since I'm the owner of that machine. Doesn't request a password either ...

---

### Post by lukeiamyourfather on 2010-11-17
If the data is really important and there's no other copy then you should probably call a data recovery expert. It will cost an arm and a leg but the chances of recovering your data are better than what you're doing now.

---

### Post by WinRiddance on 2010-11-17
Your comments aren't really helpful. Thanks anyway.

There's no doubt in my mind that the data is recoverable, it's just a matter of getting a Linux/Ubuntu expert to help out in this thread ... someone who actually works with data recovery as well as the guts of Linux/Ubuntu. I'm still searching for more options throughout the internet too and I'm sure that one way or another a solution will turn up. Please keep this thread open for someone who may be able to help with some actual step by step guidance. I'd appreciate it.

---

### Post by WinRiddance on 2010-11-18
Please  ... I know that there's got to be an expert out there somewhere ...

---

### Post by dino99 on 2010-11-18
here are the tools i use in such case:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by WinRiddance on 2010-11-18
Thanks, I've been trying to use testdisk for days but it doesn't exactly come with instructions for dummies ... 

I would like to either restore the backup data **from** my external /dev/sdb1 **to** another partition on my primary hard disk that's entitled /dev/sda3 (both of these are non-bootable data partitions) ... OR ... I'd like to restore a partial drive from my initial **testdisk.log** file in order to retrieve the most important data from partitions of my choosing to another destination of my choosing. Here's part of my problem, for example. This is taken directly from the testdisk pages:

> Image Creation From CGSecurity
In the Advanced menu, Image Creation lets you image a partition to a file named image.dd.
This command can be use for forensics purpose. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") can work on disk image and partition image, you only need to supply the filename in parameter. 
 
[LIST]
[*] Destination filesystem must have enough space to store the  file. Note that the size of the image is equal to the size of the  partition, but storing a file require more space than the filesize  because of the filesystem overhead.
[/LIST]
Well, I only need to recover apx. 75 GB of data from my 250 GB drive. But dumping the data from a 250 GB partition onto an even larger partition would require for me to buy another hard disk. There has to be a way to just retrieve the data that I need, and nothing else. I don't know how to use the command line (not the basic menu) for testdisk. Using the "auto-functions" such as copying always tries to use a default file destination that doesn't have enough space on it. I need to be able to dump data specifically from sdb1 to sda3 and nowhere else.
Any ideas about that? Thanks.

---

### Post by lukeiamyourfather on 2010-11-18
> **WinRiddance said:**
> 
Well, I only need to recover apx. 75 GB of data from my 250 GB drive. But dumping the data from a 250 GB partition onto an even larger partition would require for me to buy another hard disk.

You might want to evaluate how important this data is and get some perspective. Is it worth a few thousand dollars to you? Contact an expert if it is! Is the data maybe worth $43? If so then get another disk and copy it block by block to it so you can troubleshoot and not risk the original data (assuming it isn't already destroyed).

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152244](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152244)

If buying another disk for $43 isn't worth it to facilitate in the recovery then why are you still bothering with it?

---

### Post by WinRiddance on 2010-11-18
I'm still bothering with this for two reasons ...

ONE ... because I know there is a solution and I'm not one to just give up.

TWO ... because I, and in the future possibly others, learn something important at the same time.

Again, all you're doing is taking up completely useless space in this thread which makes it more time consuming for others to have to wade through all of these comments. I'm completely aware of the fact that there's other options as well as the cost of another hard disk. This is however a problem that I'd like to see get solved, not only for my sake but also for the future, in case someone else comes up with this kind of situation. If all of us just abandoned issues in the forums, then why come here in the first place?
Just to exchange chit chat and kill time? Nobody needs a support forum for that, right?

---

### Post by coffee412 on 2010-11-19
I have a bit of a different perspective on this problem if I may add my 2 cents here:

According to your post this is a USB drive. From my experience on most usb drive failures its not necessarily the drive that failed but the box its in. 

Remove the drive from the enclosure and you can buy a new box or just a quick connect device and see if it makes a difference.

Something like this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817801059](http://www.newegg.com/Product/Product.aspx?Item=N82E16817801059)

Or are we talking a memstick here?

---

### Post by WinRiddance on 2010-11-19
Thanks. It's actually one of those 2.5 inch mini drives and I can't even seen any screws in that housing which would permit me to open it up. I did manage to put that drive on the Vista box again, this time _invoking administrative privileges_ in order to run **chkdsk /f** on that drive. Errors were indeed found and the drive is (hopefully) being corrected as I'm writing this. Will post back later, after having the chance to test. The administrative privileges ... which I didn't have before ... were obtained by **right clicking** on the _command prompt symbol_ located under All Programs -----> Accessories.


[COLOR=DarkRed]**UPDATE:**[/COLOR]  In WindowsVista the command chkdsk /f initiated a 3 step check. At 33% during step 2 the process halted completely. However, I then reran the check differently (didn't bother to reboot), using chkdsk /R instead which implements automatic disk/file repair. This initiated a more comprehensive 5 step process of which steps 1 - 4 completed, fixing several errors. Step 5 is currently at 28% completion. Step 5 is very very slow, may not be done until later tonight.

[COLOR=DarkRed]**UPDATE 2:**[/COLOR]  Having reformatted my extra 250 GB IDE with the ext2 file system, I then ran dd_rescue (not to be confused with ddrescue i.e. gddrescue which is a different program) in order to copy the entire content of my failed sda3 partition to that 250 GB sdb1 partition. This took about 4 to 5 hours but the process just completed. In case you're interested, here's the final output from the terminal:

> root@winriddance-laptop:/home/winriddance# sudo dd_rescue /dev/sda3 /dev/sdb1
dd_rescue: (info): ipos: 209278720.0k, opos: 209278720.0k, xferd: 209278720.0k
                   errs:      0, errxfer:         0.0k, succxfer: 209278720.0k
             +curr.rate:    14324kB/s, avg.rate:    15741kB/s, avg.load: 14.3%
dd_rescue: (info): /dev/sda3 (209278752.0k): EOF
Summary for /dev/sda3 -> /dev/sdb1:
dd_rescue: (info): ipos: 209278752.0k, opos: 209278752.0k, xferd: 209278752.0k
                   errs:      0, errxfer:         0.0k, succxfer: 209278752.0k
             +curr.rate:     2722kB/s, avg.rate:    15741kB/s, avg.load: 14.3%


Although lukeiamyourfather may not learn anything at all from this thread, I'm happy to report that I've learned quite a bit in the past few days. Hopefully others will be able to use this information as well.

**BTW:** I've been around computers for around 20 years. During 12 of those years I've literally built, repaired, upgraded, and sold _hundreds_ (no typo) of computers. Out of all of those computers I've encountered a grand total of 4 bad hard disks. Now mind you, one of them was a refurbished IDE disk, another IDE went bad after a client's Son hit the computer with a football, and one of them was a 7 year old SCSI disk. Don't remember what the fourth disk was. So for those who didn't know it ... hard disks very rarely go bad, commonly lasting up to 5 and more years ... at which point most people have completely different machines/hardware anyway.

---

### Post by lukeiamyourfather on 2010-11-19
> **WinRiddance said:**
> 
ONE ... because I know there is a solution and I'm not one to just give up.


For all you know the hardware could be dying or dead and your stuff is already lost (hence recommendation to call an expert). If you're not going to call an expert you should copy whatever is left, assuming it can still be copied, to another disk and troubleshoot from there. Not every problem out there is going to be a software problem because hardware does fail. Especially hard disks. If the problem is the disk is failing then every second you use it the data is less likely to be recovered.

> **WinRiddance said:**
> 
TWO ... because I, and in the future possibly others, learn something important at the same time.


What will they learn, how not to manage backup, how not to recover files, how not to act on forums?

> **WinRiddance said:**
> 
Again, all you're doing is taking up completely useless space in this thread which makes it more time consuming for others to have to wade through all of these comments.


Gold star to you, sir. :KS

---

### Post by coffee412 on 2010-11-19
> **WinRiddance said:**
> Thanks. It's actually one of those 2.5 inch mini drives and I can't even seen any screws in that housing which would permit me to open it up. I did manage to put that drive on the Vista box again, this time _invoking administrative privileges_ in order to run **chkdsk /f** on that drive. Errors were indeed found and the drive is (hopefully) being corrected as I'm writing this. Will post back later, after having the chance to test. The administrative privileges ... which I didn't have before ... were obtained by **right clicking** on the _command prompt symbol_ located under All Programs -----> Accessories.

Some of these cases are heat sealed together. Since you cannot get the unit to respond I would force open the case and get the drive out. The drive is basically a laptop drive. You can buy an inexpensive adaptor to hook to the drive and plug into your usb port. On doing that just run fdisk - L on it and see if the partitions are there. If they are then IMMEDIATELY use something like partimage to backup the partition. Then you work with the backed up partition on a known good drive to recover. That way you dont cause any more harm to the data on the drive. 

You should know that running fsck on a disk in an enclosure with a malfunctioning adaptor card in it could alter the data and cause real unreverse-able damage to the partition or file system.

I would also like to point out to others that having an external backup drive does not provide any more safety to your data than keeping it on your main working drive. They both can fail. 

My thoughts go out to you in this time of grief. I know the feeling because I have been there myself. I really hope things workout ok and if there is anything I can do to help let me know.

coffee412

---

### Post by WinRiddance on 2010-11-19
**Alright, good news and bad news alike** ... not giving up yet though! ;)

Using the chkdsk -R method _did indeed work_ on my external USB backup disk. Once step 5 got to around 60% everything just progressed much faster. Took the drive out of the Windows setup and tried using it back on my standard Ubuntu setup, and voila, I had access to around 98% of my previously backed up data.

**Bad news is that the dd_rescue command did not appear to work** because even though the entire process came up with zero errors, I still wasn't able to access the data, directories, or anything else. Using testdisk was not a viable solution since testdisk can only copy/restore files to the current primary drive ... which in my case doesn't have anywhere near enough space on any of its partitions.

**So I'm trying something new ...**

[COLOR=Navy]Considering that all of the corrupted/missing data on my primary work partition was just that, _strictly data without an Operating System,_ I've now reformatted my extra 250 GB drive as an NTFS partition instead. This I followed up by using dd_rescue in order to dump all of the bad stuff from my primary drive onto that new NTFS partition. When that's done I'll be taking that hard disk to my Vista setup, to see if chkdsk -R will be able to restore some or all of the data for me.
It'll be interesting to see what happens, if nothing else.[/COLOR]

So as it currently stands I'm only missing about 3 weeks worth of emails and my image archive with apx. half a million images (the only things that weren't on my usb backup drive). Since my server settings are set to keep emails server wide for 14 days I should be able to retrieve all of the emails from the past 14 days as well. I'll report back when I'm done with the other drive, trying to restore data via the chkdsk -R command.

---

