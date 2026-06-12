---
title: "&quot;disc or free space is too small&quot;"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Topher88 on 2009-06-15
I'm new to Ubuntu, and I am trying to partition my hard drive and install 9.04 on my machine so that I can dual boot it with Windows XP.  It is an older computer with only 55 gigs on the hard disc, but I didn't think that would be a huge problem, but I guess i could be wrong...  I've cleared almost half of the space and now would like shrinnk the XP partition so that it's almost half and half, but when i try to do it via the Ubuntu 9.04 boot disc, I get a message that says something like "this operation has failed.  This probably happened because your disc or free space is too small."  There is only about 700MB of unallocated free space, which is obviously why I need to shrink the XP partition.  I've tried both using the boot disc and also by booting Ubuntu 9.04 from the the live CD and using the GParted Partition Editor from there, and neither method works.

I've looked around other threads on the forum, and they all act like making a GParted Live CD should be the end all solution, but I don't see how, considering that's what the boot CD uses...  But I'm making one anyway and will try it.  I'm also creating an 8.04 boot disc to see if I can get any luck with that.  I'm truly at a loss for what I need to do here, so please let me know.

Do I have to have a bigger hard drive?

---

### Post by brncao on 2009-06-15
Can you take a snapshot of your current partition map from Gparted? It's easier to assess all in one go.

---

### Post by wpshooter on 2009-06-15
After you had cleaned up your XP and before you tried to make any partition changes (resizing or otherwise), did you do at least one (and 2 or 3 passes would not hurt) pass of scandisk followed by defragmentation of your hard drive ?

---

### Post by Topher88 on 2009-06-15
> **brncao said:**
> Can you take a snapshot of your current partition map from Gparted? It's easier to assess all in one go.

I COULD...  But, with my current situation, it would be a pain because I just moved in to a new apartment (which is where the computer I'm working with is) and we don't get our internet set up for another week, so I'm using my GF's computer for internet access and not the computer that I'm trying to install Ubuntu on.  I guess if it's a must, I could try and have it by later today or tomorrow, but it consists of a lot of travelling back and forth on my part.  >.<

However, I found a copy of the exact message that I see when I try it:  It says "Failed to partition the selected disk- This probably happened because the selected disk or free space is too small to be automatically partitioned."

But anyway, I found a tutorial showing someone installing Ubuntu on a hard drive with about 30g of storage total with WinXP, so...  Like I figured, size shouldn't be a problem.  I'm going to go home and try 1) using the GParted Live CD and/or 2) trying to load 8.04 instead of 9.04.  Or if anyone has any better suggestions before then, i'll try them out as well.

---

### Post by Topher88 on 2009-06-15
> **wpshooter said:**
> After you had cleaned up your XP and before you tried to make any partition changes (resizing or otherwise), did you do at least one (and 2 or 3 passes would not hurt) pass of scandisk followed by defragmentation of your hard drive ?

I defragged once because that's all that the tutorial I was reading said to do, but no I didn't scandisk.  I guess I could try that...

---

### Post by Topher88 on 2009-06-15
Another piece of info that may or may not be relevant that I forgot to include is that my system does use a small (about 4G) FAT32 partition that Windows uses as a backup source.  It acts like it has it's own, different OS installed on it as well when I view it in GParted.  I intended on leaving it as is and not messing with it, but I don't know if that could be causing any problems in any way.

---

### Post by wpshooter on 2009-06-15
> **Topher88 said:**
> I defragged once because that's all that the tutorial I was reading said to do, but no I didn't scandisk.  I guess I could try that...

You should ALWAYS run scandisk prior to doing a defragmentation of your drive.

---

### Post by Topher88 on 2009-06-16
So...  No more suggestions???  I tried using 8.04 instead and using the GPartEd Live CD and didn't have any luck.  The hard drive simply won't allow me to partition it.

Why is it saying that my hard drive is too small if it's not?

---

### Post by brncao on 2009-06-16
Can you give us a step by step procedure on how you tried to do it in gparted? It's never failed me.

---

### Post by Topher88 on 2009-06-16
[COLOR=Red]**UPDATE:  **[/COLOR]

So, I found a user with a similar problem who got a decent resolution in [this thread,]("http://ubuntuforums.org/showthread.php?t=1106894&highlight=too+small") so I tried it out.  I was halfway successful, but it still REFUSES to shrink my XP partition and make room for Ubuntu.

The person in the above thread said that the problem was likely that there is free space at the end of the disk and Ubuntu is trying to install to that.  This makes sense, because there is about 700MB of unallocated free space at the end of my drive, so I booted GPartEd and did what he said and deleted the free space at the end and made a swap partition about twice the size of my RAM in it's place.  This worked all fine and dandy, and surprisingly enough it even shrunk the XP partition just a little bit in doing so.  However, the next thing I tried to do was shrink the XP partition enough to make room for Ubuntu, and all of the suddent it will have none of it.  So I thought "no big deal, I'll just try to partition it with the Ubuntu installation and see what happens."  I thought it was going to work this time, and then BAM!  Error message.  Now it's just telling me that it failed, it no longer gives me the "too small" message.  

I'm seriously at a loss...

---

### Post by Topher88 on 2009-06-16
[COLOR=Red]**Update #2:**[/COLOR]  

This appears to have something to do with some kind of preset that will not allow the hard drive to be partitioned past a certain point.  I was able to take the afore mentioned 700MB of unallocated space and expand it to about one gig for the linux swap, pushing the XP partition back a bit, and I soon found that I could not partition the XP partition much further past that grace period of about 1 or 2 gigs.  Until someone can russel up an explanation for why this might happen and what I can do about it, I'm at a complete loss and this installation will be halted.  As pointed out in the update before this one, it should be noted that the "too small" problem has been resolved and the problem is now that I simply cannot partition the HP hard drive past a certain, seemingly pre-set point.

> **brncao said:**
> Can you give us a step by step procedure on how you tried to do it in gparted? It's never failed me.

I did exactly what was mentioned in the thread I posted.  I got rid of the excess 700MB and created a gig of linux swap (as I only have 512G of RAM), which turned out not to be a problem.  However, on the same ticket, I attempted to shrink the XP partition enough to create a new 22G Ext 3 partition for Linux, which was not succesfull, I believe for the reason stated above.  I later deleted the 1G swap partition and fully expanded the XP partition, and later decided to shrink it back to the 700MB that it started with, which I was able to successfully.  This re-affirms that, for some reason, I am not able to shrink the XP partition past about 1G.

Any suggestions would be greatly appreciated.

---

### Post by brncao on 2009-06-16
A snapshot would be nice or you can draw it in MS paint or whatever (just the boxes to represent partitions). Is this a fresh install of Windows XP? If not, how many gb of data is in there? Is round to cylinders checked or unchecked?

[http://technet.microsoft.com/en-us/library/cc731894.aspx](http://technet.microsoft.com/en-us/library/cc731894.aspx) That could be the problem. Try backing up your data and reinstalling XP.

---

### Post by Topher88 on 2009-06-16
> **brncao said:**
> A snapshot would be nice or you can draw it in MS paint or whatever (just the boxes to represent partitions). Is this a fresh install of Windows XP? If not, how many gb of data is in there? Is round to cylinders checked or unchecked?

[http://technet.microsoft.com/en-us/library/cc731894.aspx](http://technet.microsoft.com/en-us/library/cc731894.aspx) That could be the problem. Try backing up your data and reinstalling XP.

I'll try and get a decent snapshot maybe later today, depending on how busy I am.  XP came installed on the computer, and I've been leaving "round to cylinders" checked.  

In order to re-install, I'd have to go to my old house and do some serious searching for the boot disc (unless there's another alternative).  While we're on that subject, though, if it comes to re-installation of XP, the only reason I want to keep it is because 1) I paid for it and 2) I want to have it in case I need it to fall back on for any reason.  With that being the case, provided I can find the boot disc, would I be better off just installing Linux on the whole drive and using an application like Virtual Box to install and run XP from within Linux?  Or should I just stick with dual boot?

---

### Post by brncao on 2009-06-16
If you're planning on using XP for basic stuff then yes you can use it in a virtual machine in Linux. Screen resolution is limited. You'll need to install guest additions to expand the screen resolution.

---

### Post by Topher88 on 2009-06-16
> **brncao said:**
> If you're planning on using XP for basic stuff then yes you can use it in a virtual machine in Linux. Screen resolution is limited. You'll need to install guest additions to expand the screen resolution.

Alright.  Well, as long as I have that option...  The easiest thing to do would be to partition it like I'm wanting to, so I'd still like to try and do that...  but if I have to go as far as re-installing, I guess I can settle (provided I can located the XP boot disc).  I'll try one more thing when I get home, and if possible will try and upload a snapshot.  Thanks for your help.

---

### Post by Topher88 on 2009-06-18
Okay...  I got screenshots and the "details" htm.  

Here's what it looks like before I do anything:

[ATTACH]118038[/ATTACH]

Here's what I want to do:

[ATTACH]118039[/ATTACH]

Here's the error message:

[ATTACH]118040[/ATTACH]

And here are the details:

GParted 0.4.3
 Libparted 1.8.8


    **Shrink /dev/sda2 from 51.08 GiB to 30.26 GiB**  00:00:37    ( ERROR )             calibrate /dev/sda2  00:00:00    ( SUCCESS )             [I]path: /dev/sda2
start: 8573040
end: 115698239
size: 107125200 (51.08 GiB)[/I]          calculate new size and position of /dev/sda2  00:00:00    ( SUCCESS )             [I]requested start: 8573040
requested end: 72031679
requested size: 63458640 (30.26 GiB)[/I]       [I]new start: 8573040
new end: 72031679
new size: 63458640 (30.26 GiB)[/I]          check file system on /dev/sda2 for errors and (if possible) fix them  00:00:12    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 54848098816 bytes (54849 MB)
Current device size: 54848102400 bytes (54849 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 24832 MB (45.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     53674 MB             0
Multi-Record       :     54514 MB        143756
$MFTMirr           :      7343 MB             1
Compressed         :     54509 MB        137535
Ordinary           :     54516 MB         65330
You might resize at 24831565824 bytes or 24832 MB (freeing 30017 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:00:13    ( ERROR )             run simulation  00:00:13    ( ERROR )             ***ntfsresize -P --force /dev/sda2 -s 32490823679 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 54848098816 bytes (54849 MB)
Current device size: 54848102400 bytes (54849 MB)
New volume size    : 32490816000 bytes (32491 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 24832 MB (45.3%)
Collecting resizing constraints ...
Needed relocations : 2272179 (9307 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1040 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sda2 for errors and (if possible) fix them  00:00:11    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 54848098816 bytes (54849 MB)
Current device size: 54848102400 bytes (54849 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 24832 MB (45.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     53674 MB             0
Multi-Record       :     54514 MB        143756
$MFTMirr           :      7343 MB             1
Compressed         :     54509 MB        137535
Ordinary           :     54516 MB         65330
You might resize at 24831565824 bytes or 24832 MB (freeing 30017 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:01    ( SUCCESS )             run simulation  00:00:00    ( SUCCESS )             ***ntfsresize -P --force /dev/sda2 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 54848098816 bytes (54849 MB)
Current device size: 54848102400 bytes (54849 MB)
New volume size    : 54848098816 bytes (54849 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:01    ( SUCCESS )             ***ntfsresize -P --force /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 54848098816 bytes (54849 MB)
Current device size: 54848102400 bytes (54849 MB)
New volume size    : 54848098816 bytes (54849 MB)
Nothing to do: NTFS volume size is already OK.[/I]

---

### Post by merlinus on 2009-06-18
Even if you defragged the windows partition, the paging file may be taking up space at the end of it, so it cannot be resized.  You would need to disable the paging file, reboot, defrag, shrink the partition, and then reinstate paging.

---

### Post by Topher88 on 2009-06-18
> **merlinus said:**
> Even if you defragged the windows partition, the paging file may be taking up space at the end of it, so it cannot be resized.  You would need to disable the paging file, reboot, defrag, shrink the partition, and then reinstate paging.

Okay.  I already tried disabling the paging file, but it didn't do any good, but I didn't defrag afterwards, so I might go ahead and let it defrag overnight and try again tomorrow.

But one quick question...  Is the paging file actually located somewhere so that I could temporarily move it like the articles suggests?  Because that seems like it would be easier...  But if not, I'll just defrag and give it another go tomorrow.  Thanks!

---

### Post by merlinus on 2009-06-18
Don't believe you can move it.  It shows up as unmovable system files, a green rectangle in the defrag box near the end of the partition, at least on win2000.  You can restore it afterwards, as not having it will probably make windows even slower.

---

### Post by Topher88 on 2009-06-18
> **merlinus said:**
> Don't believe you can move it.  It shows up as unmovable system files, a green rectangle in the defrag box near the end of the partition, at least on win2000.  You can restore it afterwards, as not having it will probably make windows even slower.

A'ight, I defragged overnight, and when I checked it this morning it said it was complete but some files couldn't be moved.  I'll check and see where that green file is this time and try the installation once again...

---

### Post by Topher88 on 2009-06-18
> **merlinus said:**
> ...disable the paging file, reboot, defrag, shrink the partition, and then reinstate paging.

This worked!  I successfully shrunk the partition using the 9.04 install disk and installed Ubuntu on the new partition!  Thanks!

---

### Post by merlinus on 2009-06-18
Excellent!  Good on you for keeping at it until success.

Happy ubuntuing, and post back if you run into other difficulties.

---

