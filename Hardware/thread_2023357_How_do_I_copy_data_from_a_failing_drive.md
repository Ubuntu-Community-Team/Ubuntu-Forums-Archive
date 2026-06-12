---
title: "How do I copy data from a failing drive"
date: 2012-07-12
forum: Hardware
---

### Post by NubunTony on 2012-07-12
Hi, I had a problem with Windows 7 not loading so I took the plunge and installed ubuntu (for the first time) yesterday after installing a new hard disk - works fine, albeit strange (to me)! It seems the "W7" problem was (as ubuntu tells me after I installed it as a second drive) the old drive is imminently going to fail. My question is, how do I access the data on that disk and copy it to my new drive?

Would it help if I also installed Windows on the new drive (not sure how to do that - didn't partition disk before installing ubuntu)

---

### Post by ahallubuntu on 2012-07-12
You can access your Windows 7 drive from Ubuntu to copy files, if the drive hasn't completely failed yet.  Just note that the more you use your failing drive, the more wear you put on it and the closer you bring it to complete failure (unable to access anything).

Most if not all of your important files should be stored in the C:\Users\YOURNAME folder in Windows .  It won't be called C: in Ubuntu though - and Linux uses / not \ for directories.  So you will see it as /Users/YOURNAME on your Windows drive.

---

### Post by David Andersson on 2012-07-12
> **NubunTony said:**
> My question is, how do I access the data on that disk and copy it to my new drive?


If failing means it has bad blocks, and it gets worse by time, use command **ddrescue** in package **gddrescue**. It will copy most of the good blocks relatively quickly, and then it will try to copy remaining blocks closer to the faulty blocks. See [http://ubuntuforums.org/showpost.php?p=12044030&postcount=8](http://ubuntuforums.org/showpost.php?p=12044030&postcount=8)

While you set things up for ddrescue, keep the bad disk spinned down, or powered off, or with good air flow for cooling. If you think it will not spin up again if spinned down, don't spin down, just keep it well cooled.

You can copy to a partition on another disk. The partition must be of the same size or larger. Or you can copy to a file, which must be on a file system with enough free space to hold the copy of the entire partition. If you copy to a partition you can try run fsck on it and try mount it. If that works you can access all files that hasn't been damaged. And files that may have been damaged inside too.

If you just mount the bad drive and start copy files, per previous comment, and it turns out it cannot copy certain files, you can use ddrescue to copy just those files. See [http://ubuntuforums.org/showpost.php?p=10863270&postcount=60](http://ubuntuforums.org/showpost.php?p=10863270&postcount=60)

(Those copied files will likely be damaged inside, but sometimes a bad copy is better than none at all.)

---

### Post by NubunTony on 2012-07-12
> **ahallubuntu said:**
> You can access your Windows 7 drive from Ubuntu to copy files, if the drive hasn't completely failed yet.  Just note that the more you use your failing drive, the more wear you put on it and the closer you bring it to complete failure (unable to access anything).

Most if not all of your important files should be stored in the C:\Users\YOURNAME folder in Windows .  It won't be called C: in Ubuntu though - and Linux uses / not \ for directories.  So you will see it as /Users/YOURNAME on your Windows drive.

Thanks for this, however I can't see how to find the (data on the) old drive and I don't know whether that's due to the disk problem or because I don't know where to look using ubuntu: in Windows I'd look under "Computer" to find all of the drives and then take it from there but, in ubuntu, all I can (readily) see is "Home Folder" and the "Desktop" folder has nothing in it.

---

### Post by NubunTony on 2012-07-12
> **David Andersson said:**
> If failing means it has bad blocks, and it gets worse by time, use command **ddrescue** in package **gddrescue**. It will copy most of the good blocks relatively quickly, and then it will try to copy remaining blocks closer to the faulty blocks. See [http://ubuntuforums.org/showpost.php?p=12044030&postcount=8](http://ubuntuforums.org/showpost.php?p=12044030&postcount=8)

While you set things up for ddrescue, keep the bad disk spinned down, or powered off, or with good air flow for cooling. If you think it will not spin up again if spinned down, don't spin down, just keep it well cooled.

You can copy to a partition on another disk. The partition must be of the same size or larger. Or you can copy to a file, which must be on a file system with enough free space to hold the copy of the entire partition. If you copy to a partition you can try run fsck on it and try mount it. If that works you can access all files that hasn't been damaged. And files that may have been damaged inside too.

If you just mount the bad drive and start copy files, per previous comment, and it turns out it cannot copy certain files, you can use ddrescue to copy just those files. See [http://ubuntuforums.org/showpost.php?p=10863270&postcount=60](http://ubuntuforums.org/showpost.php?p=10863270&postcount=60)

(Those copied files will likely be damaged inside, but sometimes a bad copy is better than none at all.)

Thanks David, I'll take a look at [B]gddrescue.
[/B]
I've had a look and, sofaras I understand it, my problem is that I don't know how to find the address of the old drive - that may be due to the fault. Ubuntu tells me the disk is about to fail - at least I hope it's the old, rather than the new one! - I think I need to find out how to view the drives in ubuntu, that is, what their addresses are. 

I haven't (re) installed Windows (should I?)

---

### Post by NubunTony on 2012-07-12
Mwching around in the system I have found the relevant device  is /dev/sdb1 (and "DISK FAILURE IS IMMINENT"!) so I've downloaded gddrescue and am just going to run it to see if this works (gets me an image of the old disk). Thanks for your help

---

### Post by americanman28 on 2012-07-12
Plug both drives in and transfer from 1 to the other from what OS is installed on the good drive.
Good Luck

---

### Post by NubunTony on 2012-07-13
> **NubunTony said:**
> Mwching around in the system I have found the relevant device  is /dev/sdb1 (and "DISK FAILURE IS IMMINENT"!) so I've downloaded gddrescue and am just going to run it to see if this works (gets me an image of the old disk). Thanks for your help
I left it running overnight and the last message I have is:

[COLOR=DarkGreen]Current status
rescued:    58846 kB,  errsize:  46010 kB,  current rate:        0 B/s
   ipos:    24713 kB,   errors:      61,    average rate:     1700 B/s
   opos:    24713 kB,     time from last successful read:     9.8 m[/COLOR]
[COLOR=DarkGreen]Splitting failed blocks...[/COLOR]

[COLOR=Black]Err .. I think that's what it said when I went to bed - how do I know when it's finished (I guess there will be some message to that effect) and how do I look at and retrieve data?
Sorry to be so wet, just a stranger in a strange ubuntu world.
[/COLOR]

---

### Post by David Andersson on 2012-07-13
> **NubunTony said:**
> I left it running overnight and the last message I have is:

[COLOR=DarkGreen]Current status
rescued:    58846 kB,  errsize:  46010 kB,  current rate:        0 B/s
   ipos:    24713 kB,   errors:      61,    average rate:     1700 B/s
   opos:    24713 kB,     time from last successful read:     9.8 m[/COLOR]
[COLOR=DarkGreen]Splitting failed blocks...[/COLOR]


I think "Splitting failed blocks" indicates that it has gone into its second pass. During the first pass it should have rescued most of the good blocks. It says "rescued: 58846 kB" and "errsize: 46010 kB" which I think means only about 56% was rescued in the first pass. The second pass will likely rescue more, but you must be prepared that quite a high percentage can be lost.

It will take some time. Say copying a healty hard disk takes about 1/2 hour. Reading and writing each block take milliseconds. If there are bad blocks, each bad block can take 10-30 seconds before the read attempt gives up. If there are 1000 bad blocks the process will take 3-10 hours. You may have more than that, so be prepared to wait quite a few many hours.

Are you copying to a file (disk image file) or to an empty partition?

---

### Post by NubunTony on 2012-07-13
> **David Andersson said:**
> I think "Splitting failed blocks" indicates that it has gone into its second pass. During the first pass it should have rescued most of the good blocks. It says "rescued: 58846 kB" and "errsize: 46010 kB" which I think means only about 56% was rescued in the first pass. The second pass will likely rescue more, but you must be prepared that quite a high percentage can be lost.

It will take some time. Say copying a healty hard disk takes about 1/2 hour. Reading and writing each block take milliseconds. If there are bad blocks, each bad block can take 10-30 seconds before the read attempt gives up. If there are 1000 bad blocks the process will take 3-10 hours. You may have more than that, so be prepared to wait quite a few many hours.

Are you copying to a file (disk image file) or to an empty partition?

Just checked this site before  going to bed. 

I've copied to a disk image file and I'm just downloading furiusisomount which I hope will let me read the file - I've disconnected the old drive but appreciate that, if this doesn't work. I'll need to reconnect it and try again/ further gddrescue, but I'm going to get some sleep and come back to this with a clear(er) head in the morning. Thanks for your help

---

### Post by ijumpship on 2012-07-13
keep this in mind if all fails

Good for Rescue

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

### Post by David Andersson on 2012-07-14
> **NubunTony said:**
> 
I've copied to a disk image file and I'm just downloading furiusisomount which I hope will let me read the file -


I assume you have copied the partition to an image file with a filename like "blabla.img".

(Alternative to FuriusIsoMount) You can try mount the disk image with this command
```
sudo mkdir /media/blablabla
sudo mount -o ro,loop blabla.img /media/blablabla
```

("ro" is for read-only)

If important file system blocks have been successfully recovered you may be able list files and folders in /media/blablabla and maybe open some files.

When you are done, unmount with
```
sudo umount /media/blablabla
sudo rmdir /media/blablabla
```

With FuriusIsoMount you can do the same, but with a graphical interface, and probably without sudo.

If there are as many bad blocks as your next to previous comment suggests, it may be problematic to mount the disk image file.

(Maybe) You may want to try a file system check, to correct blocks needed to list files and folders. I assume the disk (and the image) contains an NTFS filesystem, so a proper file system check has to be done in Windows. (Which means you must make the disk image, currently on a linux file system I assume, available to Windows. If you have a big spare partition on a healthy disk, cat, dd, or cp the image to that partition and let Windows see it.)

(Request) Can we see the final printout from the ddrescue command?

> **NubunTony said:**
> 
I've disconnected the old drive but appreciate that, if this doesn't work. I'll need to reconnect it and try again/ further gddrescue,

I'll suggest you let ddrescue run as long as it wants. After 2 or 3 passes it will finish by itself. But it may take a very long time for it to complete, depending on the number of bad block. You can pause it with Ctrl-C and restart it with the same command while in the same folder, but I think you could let it run while you sleep to save time. If you want to maximize the the number of recovered blocks I see no reason to stop ddrescue before it has finished pass 2. (Unless there is a real world deadline imposed, at which time you simply must accept what you have got so far. Or, the disk havn't moved for hours and it is obvious it has become stone dead.)

Did you let ddrescue run until the end, or did you stop it?

(If) If you stopped ddrescue before it was complete, start it again with the same command, and go to sleep. (Do not remove the image file or the log file. When kept, ddrescue will continue where it left off.)

(If) (If you told ddrescue to re-try a number of times, you can stop it if it has gone into its re-try pass. The re-try pass is much less likely to recover more blocks, compared to the first two passes. There you can make a reasonable trade-off, between time and amount of recovered data.)

---

### Post by mike acker on 2012-07-14
> **NubunTony said:**
> Hi, I had a problem with Windows 7 not loading so I took the plunge and installed ubuntu (for the first time) yesterday after installing a new hard disk - works fine, albeit strange (to me)! It seems the "W7" problem was (as ubuntu tells me after I installed it as a second drive) the old drive is imminently going to fail. My question is, how do I access the data on that disk and copy it to my new drive?

Would it help if I also installed Windows on the new drive (not sure how to do that - didn't partition disk before installing ubuntu)
~~
I would try SPINRITE (Gibson Reserarch )

The motherboard (ASUS M5A88-M) that I have on my PO for my U-Box build project has RAID support (0/1/5/10) . accordingly I put 2 hardrives on the P.O. ...

I have wondered for some time why desktop PCs didn't offer RAID 1

I guess you could sign up for Carbonite or such but if you could have RAID1 you wouldn't have to worry about Carbonite having their worm in the guts of your system

---

### Post by NubunTony on 2012-07-18
> **NubunTony said:**
> Just checked this site before  going to bed. 

I've copied to a disk image file and I'm just downloading furiusisomount which I hope will let me read the file - I've disconnected the old drive but appreciate that, if this doesn't work. I'll need to reconnect it and try again/ further gddrescue, but I'm going to get some sleep and come back to this with a clear(er) head in the morning. Thanks for your help

It didn't let me read the file so I've decided to buy a caddy for my old hard drive and see if I can read anything from it externally via USB. 

I'm enjoying the ubuntu experience, however finding annoyance at things like the printer on the all-in-one Kodak ESP 5250 working but not the scanner: lucky I have a laptop running Vista and dropbox as a work-around until I have the time to research and resolve. I hope I'm not annoying experienced users by asking questions I should know the answer to and hope someone may be able to point me to an idiots guide to ubuntu/ linux - for example I've no idea what an image file is.

---

### Post by ahallubuntu on 2012-07-18
One thing to understand about Linux is that not all hardware is supported equally well.  Some hardware works automatically and more smoothly than in Windows; drivers are already in the kernel so there is none of this "Hey, I need a driver...hey let me look for that...." nonsense.  But other hardware works poorly or not at all.  

How well it works depends on the manufacturer.  Windows doesn't write most device drivers; the manufacturers do.  When you bought your Kodak printer, you probably got a CD with it.  You had to install a driver most likely (unless the printer is really old).  In many cases, manufacturers do not include any Linux driver on that CD. If you're lucky it will just work in Linux when you plug it in or you might at least have the option to download a driver.

I have a Canon All-In-One printer.   Plug it in in Ubuntu 10.04 LTS and no support.  Fortunately for me, I found a driver for it on Canon's Europe site (not sure why not on the US site).  The driver works great for many things (like printing wirelessly, which I do the most) but not for certain things like scanning wirelessly or printing in B&W.  Those things do work in Windows.

What I do for cases like this is to run Windows in a virtual machine within Ubuntu.  If I want to scan wirelessly, I start up virtual XP (using Oracle's Virtualbox), where I have installed the printer and scanner driver software from Canon.  That works very well.  Virtual XP is just a window I (basically) close when I'm done and I'm still in Ubuntu.  I had to spend some time installing XP at first in Virtualbox but now I just double-click to start it up occasionally.  Really sweet.  You might consider the same for your Kodak scanner if you can't get it to work natively in Ubuntu.

---

### Post by David Andersson on 2012-07-18
> **NubunTony said:**
> It didn't let me read the file 
**Questions**

What didn't? FuriusIsoMount? Did it say why? (error message?)

Did you try the "sudo mount" command? Did it fail too? Did it say why?

You havn't answered how far you let ddrescue run? What was its last message? If you post its log file, we may be able to tell if it had completed copying of all non-faulty blocks. (You can post the log in [http://pastebin.com](http://pastebin.com) or [http://paste.ubuntu.com](http://paste.ubuntu.com) and provide a link to it in a comment here.) If it had, the image file is now your best source to continue rescuing files and data.

> **NubunTony said:**
>  so I've decided to buy a caddy for my old hard drive and see if I can read anything from it externally via USB. 
I don't think a *hard disk caddy* will help. It won't be able to read faulty blocks any more than the sata or ata in your computer already have done.

If you feel uncomfortable with doing the rescuing yourself, and the data was really important, there are *companies* specialized in rescuing files from damaged drives. You send them the drive and they analyze it and will tell you a price. If will cost at least a few hundred dollars, often much more, depending on how difficult it will be. The first thing they do, if they find it appropriate, is basically what you've done already, copy the data off with ddrescue or similar. (I don't know which company to recommend, but do some research before selecting one.)

> **NubunTony said:**
> I hope I'm not annoying experienced users by asking questions I should know the answer to 

No problem. It's part of the learning process. Really.

> **NubunTony said:**
> an idiots guide to ubuntu/ linux 

When I search for "linux guide" there are scores of sites. I don't know which one is best, so you have to try them all, or wait for someone else to answer.

> **NubunTony said:**
> - for example I've no idea what an image file is.

It's the same in Windows. An *image file*, also known as *disk image file*, is just a *file* that is a *copy* of an entire *hard disk partition* or *drive* (or an optical medium such as a CD). The hard disk is a data storage that logically is a long sequence of billions of bytes. (The concept of a "file system" is a way to organize folders and files in that storage space.) A file is also a sequence of bytes, so it is possible to make an exact copy of all data in a partition or drive (or CD) and save it in a file. If the drive or partition was 150GB in size, the image file will be 150GB too.

You can name an image file whatever you want, but normal file name suffixes are ".img" and (for CD images) ".iso".

A completely *different* meaning of *image file* is a file containing an picture. You know, jpeg, gif, png, bmp.

---

