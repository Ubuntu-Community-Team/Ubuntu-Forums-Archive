---
title: "HDD disappeared?"
date: 2011-02-17
forum: Hardware
---

### Post by prayersfor.rain on 2011-02-17
Sorry if this is in the wrong forum, I wasn't sure where to put it.
I've got ubuntu 10.10 and winxp.
Up until an hour ago, the 2tb hard drive I use for storage was showing up in "places".  Now I've got nothing.  It was formatted ext3 or something like that.  I went into winxp to see if it'd show up, got into disk management, and it saw my drive but said it was unallocated. I tried creating a partition, and then it showed up, but only that partition I made.

Got back into ubuntu and that partition I created with winxp shows up, but nothing with any of my files (which I assume are "unallocated").
I did some sort of fdisk command and the drive shows up but it said something about how there's no partition.

I really don't want to format the entire thing or anything, there's a lot of stuff on there.
And, this drive has shown up for the past 2 weeks, that was when I hooked it up and transferred files from another drive, etc.  And all of a sudden when I tried to select an .iso file from the drive with Furius the drive just disappears.

Any help would be great.  Maybe I've not been using the correct search terms, I haven't really found anything.

---

### Post by Grenage on 2011-02-18
Hi there,

First point of order, make no further changes to the drive; no partition edits or data writes of any kind.

I don't know what happened to your drive; it could have been a drive fault, accidental erasure, or hell pixies.  The applications you'll probably want to use are Testdisk and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), which recover partitions and data respectively.

I don't think that the names of recovered files are restored, but the data should be.

---

### Post by fvds on 2011-02-18
Hi there,
To me it seems you did over-write your ext3 partition information when you created a partition in Win XP. Win XP is not aware of any linux partition.
When you want to share a drive with Win XP you should not use a Linux specific partition type like ext3, but switch to NTFS or FAT(32).

The upside is, this is not a drive failure of any hardware kind, the downside is, that you caused this yourself.

I'm not sure how to recover from this, however there is some documentation on this subject:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I wish you all the luck you need!

Fred

---

### Post by prayersfor.rain on 2011-02-18
Well, I kinda knew that ext3 wouldn't work well with WinXP.  I wasn't expecting it to work there.  I need it to work in Ubuntu because that's what I use mostly.
 
The strange thing is that before I even messed with the drive (created that new Windows partition and etc), it disappeared in Ubuntu.  Basically it was showing up in Places, I clicked on it and all of a sudden it vanished.  I hadn't made any changes whatsoever to the drive other than *format, transfer files, plug in* when it disappeared.  I don't even think I've saved anything new on that drive since installing it and that was like 2 weeks ago.
 
The only reason I even logged onto WinXP was to see if the drive would show up at all.  I've NEVER accessed that drive through WinXP ever - it's a brand new drive (I guess) that I got through warantee with WD about 3 weeks ago and yesterday was the very first time I booted Windows with that drive attached "plugged in" (but not showing up in either OS).
 
So yeah, the drive just disappeared, **before** I ever got on WinXP and modified things. 
 
I don't get it.  I could access it for 2 weeks, It worked ok and then disappeared IN LINUX without me changing anything, before I ever booted WinXP.  How does a linux partition just disappear?  It's like it went from being ext3 to nothing.
:(
 
Is there any way to recover data and save it onto that same drive?  I don't have 1.5TB free to transfer all of my files to while I reformat and I don't have money to get another drive right now.  
 
Oh hey thanks for the responses so far.   :)

---

