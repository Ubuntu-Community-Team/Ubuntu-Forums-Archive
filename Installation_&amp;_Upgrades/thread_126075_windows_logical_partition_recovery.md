---
title: "windows logical partition recovery"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by pablovp on 2006-02-05
Hi

My disk had 2 fat32 partitions, a primary partition and a logical one.

To create a new reiserfs partition i deleted the primary fat32 partition, and created two new partitions, a new primary fat32  and a reiserfs partition.

the logical fat32 was left untouched...

But now i can't access the fat32 logical partition, can i recovery it?

i'm i little bit crazy about losing my mp3 collection... :cry:

---

### Post by Herman on 2006-02-05
FAT32 partitions are great because even if you delete everything out of them there is a program called 'fatback' which can recover it all again in a flash. You probably won't even need that though. 
I'll bet you can still access all your files from a 'live' cd.
I'll also bet your only problem is likely your partition numbers have changed when you deleted, then added partitions. Probably all you need to do is update your text file called 'fstab' in your /etc directory).

 (It's funny the logical partition number would be changed if you only changed primary partitions though. Did you have a swap area also that might have been logical and you did something to that one?) It doesn't matter, anyway, all you probably need to do is this:
1) Start up you partitioner again just for a look at the new partition numbers and this time make a note of them. (Like on a scrap of paper). Then exit the partitioner.
2) Boot into Ubuntu again and open a terminal and open your /etc/fstab file like this:```
sudo gedit /etc/fstab
``` Then, check to see if your partition numbers listed in /etc/fstab are correct.
If they are different from what your notepaper says they should be, then delete the old numbers which are no longer correct and replace with your new partition numbers that you have written down on your notepaper.
Then click 'save' and exit the text editor.
3)Restart your computer and see if everything is back to normal.
If I am right, that should have fixed it. (I hope) 
Please post back and let us know how you get along. Either me or someone else can help you more if you need more help. :-D (Herman)

---

### Post by pablovp on 2006-02-05
It didn't work...

Here is my fdisk /dev/hda output: 

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2675    21486906    c  W95 FAT32 (LBA)
/dev/hda2            2676        3404     5855692+  83  Linux
/dev/hda4            3405       12161    70340602+   5  Estendida
/dev/hda5            4134       12161    64484910    b  W95 FAT32
/dev/hda6            3405        4073     5373679+  83  Linux
/dev/hda7            4074        4133      481918+  82  Linux swap / Solaris

Logical partitions at wrong order.

Windows don't recognize the partition and i can't mount it on linux too.

Here is the output from dmesg:

[4301634.630000] VFS: Can't find a valid FAT filesystem on dev hda5.

---

### Post by Herman on 2006-02-06
What does the output say when you open a terminal and type: ```
sudo parted /dev/hda
``` and then you type ```
p
```?
(Press q to quit parted, just in case you aren't sure.)
I wonder if your hda7 swap ending at 4133 might be just overlapping your hda5 beggining at 4134, but we can't see it. According to [this]("http://www.ranish.com/part/primer.htm"), your vfat file allocation tables would be there. In [this thread]("http://www.ubuntuforums.org/showthread.php?t=124554"), meono solved a problem by deleting the swap area. Although your problem seems a little different, I wonder if that might work? It would be an easy thing to try, and wouldn't do any harm. Just deleting it and making one again might just work. You did not say you did anything to either of those two partitions, and they seem like they are a long way from the ones you did work on. That's strange.
After reading [this]("http://www.ata-atapi.com/hiwtab.htm"), I am wondering if sometimes after we use two or three different softwares from different partitioner makers, that all disagree with each other just by just a small amount, whether those differences are enough to add up to a small mistake in our partition tables. It happened to me once after mixing lots of different brands of partitioning softwares.
I tried simulating your partitioning scheme on a test computer, but I have had no results yet with fatback, I remember now when I was practicing with it a long time ago, I was using it on operating systems, it would recover files that were deleted from the rubbish bin. That's a lot different from a data partition. I'm probably not typing the right commands. I'm not sure how it works anyway, maybe it won't work if it can't find the file allocation tables. 
See what output you get from reading the tables with parted, thanks. (Herman)

---

### Post by pablovp on 2006-02-06
Here is the output:

Using /dev/hda
(parted) p
Disk geometry /dev/hda: 0.000-95396,273 megabytes
Disk label type: msdos
Minor    Beggining             End              Type        File System  	  Sinal
1          0,031            20983,337          primary        fat32               lba
2      20983,337            26701,787          primary        reiserfs
4      26701,787            95393,781          extended
6      26701,849            31949,582          logical        reiserfs
7      31949,613            32420,236          logical        linux-swap
5      32420,237            95393,781          logical

---

### Post by pedwards on 2006-02-06
you might want to try the wiki for mounting partitions , i found it super helpful. especially with mounting irregular disks.

---

### Post by Herman on 2006-02-07
Yes, pedwards makes a good point. I am presuming a lot of things about this that maybe have not been made clear enough. It is my fault for not asking more questions sooner.
Is this the situation?
You had Windows on               28.0 GB  on hda1. 
You had Ubuntu 'Breezy' on     5.0 GB        hda6
With a swap area                      0.5 GB   on hda 7
and a FAT data partition,         66.0 GB  on hda5
                                                99.5 GB    total
You decided Windows on hda1 had too much room, and you resized your Windows hda1 partition with some kind of partitioning software, down to 22.0 GB. Then, you used this software to make yourself a new reiserfs data partition (primary) 6.0 GB.
Now, are still using the same installation of Ubuntu 'Breezy' on hda 6, but you can no longer access the FAT32 data partition hda5, which you used to be able to access before running the partitioner.
You used to be able to access this same partition from your Windows installation too, and now you can not. 
Is this all correct?
Or am I making assumptions I shouldn't be making?
How many GB of data was on hda5? 
Have you tried mounting the partition with a Live CD?
Does the partition look normal when viewed with whatever partitioning software you used, if it was one with a graphical representation of your partitions? 
Can you 'see' the data in it with the partitioningsoftware? Can we resize it to a smaller size so as to be able to manouvre it if we decide to? Or was it completely full with mp3s?
What level of risk of losing the data are you willing to take in order to try to recover compared with how much time it takes. (Do you feel like taking a risk to try things we aren't sure will work, or do you want to be very careful?) 
I have a couple of ideas we could try, not I'm not certian they will work for sure or not.     ??? Regards, :-D (Herman)

---

### Post by pablovp on 2006-02-07
> Is this the situation?

Kind of...

That was my partition scheme:
windows ntfs on 25.5 GB on hda1.  
ubuntu dapper reiserfs on 7.7gb on hda2
boot partition(ext3) on 50mb on hda3
swap area on 256mb on hda4
FAT data partition, 66.0 GB on hda5 

I decided to rezize hda1(win) to 22 gb, removed hda1,2,3,4 and created a 22gb fat32 partition at hda1, a reiserfs(breezy) of 5.5gb on hda2, a reiserfs(dapper64) of 5.0gb on hda6 and a swap area of 500mb on hda7, all of that using breezy installation partitioner.

> You used to be able to access this same partition from your Windows installation too, and now you can not. 
Yes, i can see my data partition on windows, but it's "not formated", so i can't access data.

> Have you tried mounting the partition with a Live CD?
No, but i will try.

> 
Does the partition look normal when viewed with whatever partitioning software you used, if it was one with a graphical representation of your partitions?
Gparted list the partition as unknow type.

Maybe the order of the partitions are important to mount it? sorry but im no expert on that, fdisk said that "logical partitions out of order".

> What level of risk of losing the data are you willing to take in order to try 

The data on the partition is very important to me, if a can backup before testing dangerous things it would be great
I don't care to install all of my systems again as long i have my data partition working,so im careful on it.

Sorry for being verbose.

---

### Post by Herman on 2006-02-09
>  The data on the partition is very important to me, if a can backup before testing dangerous things it would be great
I don't care to install all of my systems again as long i have my data partition working,so im careful on it.
Sorry for being verbose. Okay, don't be sorry for being verbose, your story contians valuable clues to help me piece together a picture of what might be wrong. Your user profile and previous posts tell a story too, I use those to help me to help people quite often.

Right then! You should first, (if you want to be safe), buy another hard disk and 'dd' your old hard-disk to the new one, or at least the damaged partition you want to back up and later try to rescue. You will only need to try to rescue one copy of it, so if the rescue method fails, or damages it, you still can 'dd' a new copy back again.
I was unable to (using my test computer) force any 'parted' based partitioner to do what I think has happened to you, (overwrite your FAT tables), they all just refuse to do it, no matter how hard I try.
I was able to find a command to write zeros to the first 8 sectors of hda6, to erase the fat tables and produced similar symptoms. 
Unfortunatley, it makes my old 'book pc' (pictured in my avatar) very unstable, preventing further testing. I got only a few re-boots before it refused to co-operate any further. Once I deleted the problem partition with [GParted livecd-0.2]("http://gparted.sourceforge.net/livecd.php"), and created a new one, the test computer was back to normal. Maybe it's old antiquated BIOS is not able to cope with this type of error as well as your newer AMD64 machine's more modern one.
 Another thing, I'm not sure if even a 'dd' command will work. The 'copy' option came up grey in my GParted, and I think it employs the 'dd' command to do the actual work, I'm not sure, but I hope you'll be able to make a back-up that way.
Even if it doesn't work, another hard disk would _not_ be a bad investment if you like testing new softwares. You will be able to use it in future to perform back-ups _before_ the damage is done instead of later.
Your problem is something similar to the damage I have read can be done by the 'CIH' virus, or a variant of it. You should also file a bug report with 'Dapper' developers just in case they are improving the installer/partitioner and a bug in the improvements could have caused the problem. (As I said in an earlier post, your swap might have overwritten the first bit of this partition, covering up your fat tables.)
The most promising looking solution I was able to find by googling, was [this one]("http://grc.com/cih.htm").
Unfortunately, it's a Windows based program, and although I downloaded a copy to try it out, I can't get Windows 98 to install in the test computer without wiping out the whole hard drive. I'm not quite ready for that at this particular point in time. Even if it is only a test computer, I have a couple of nice 'Breezy' installs already in it that I want to use for some other things in the immediate future.
 It would be good if I had a Windows 98 liveCD to run the repair floppy from. (only joking) :-D.
Well, Pablovp, I hope this helps you, let me know if I can help you any more, (any question, please ask). I have found this very interesting and learned a lot so far. I wanted to get this reply in in case you thought I had forgotten you. Good luck with it, regards, :-D (Herman)

---

### Post by pablovp on 2006-02-09
Thanks herman, im glad for your help.  :) 

I will try copying my files to other harddisk, then i will try to erase all my partitions (excluding my fat32 data) and recreate them the order before the accident.

If  i fail i will try to use the Cih recovery, if i fail again i will be not happy. :neutral: 

Anyway, thanks a lot dude!

---

### Post by Herman on 2006-02-09
>  If i fail i will try to use the Cih recovery, if i fail again i will be not happy. Well, as long as you have the original back-up of the partition like I said, if one recovery method doesn't do it, just re-copy it and try another. 'You never fail until you give up.' There are hundreds of recovery softwares available to choose from, that one looks like the most likely of all I looked at. I am sure you will succeed eventually. Some people who deliberately intend  to destroy data for one reason or another seem to find that difficult to do, they need to work at it. So recovering data that is only accidentally destroyed should be possible. We might have to work at it though. 'Keep your chin up', and don't give in, :-D (Herman).

---

### Post by shane2peru on 2006-02-11
I happened across this thread, when I had a very similar problem.  I know this is not a "Linux" solution, but when your data is on the line, just about any solution will work.  I came across this free program:  PC Inspector (for windows)  at:  [http://www.pcinspector.de/file_recovery/uk/welcome.htm](http://www.pcinspector.de/file_recovery/uk/welcome.htm)   I was able to recover all my data off my Fat 32 partition.  It is a free program, and it works!  So all you need now, is a MS OS to recover, and if you lost fat32 data, that means you probably have a MS OS somewhere.  Hope this helps someone.

Shane

---

### Post by pablovp on 2006-02-20
Solved the problem.

I used "Active Undelete" a non-free application for windows to do that, pc inspector crashed several times with invalid memory acess errors.

Active undelete gave me access to the damaged partition, but did not rebuild the fat table, so i had to recreate the partition after the backup.

---

### Post by Herman on 2006-02-20
Thank you for letting us know it's fixed and how you fixed it. I'm glad to hear you got all your music back! :D 
[Active Undelete]("http://www.active-undelete.com/") eh? Well done! :-D (Herman)

---

