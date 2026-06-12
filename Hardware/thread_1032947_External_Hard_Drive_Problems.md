---
title: "External Hard Drive Problems"
date: 2009-01-06
forum: Hardware
---

### Post by evw2k on 2009-01-06
Okay so I have a 1TB Buffalo external hard drive that I hooked up over firewire with a bunch of my music and DVD collection backed up on it.  It was working fine in Vista, so I changed iTunes to store my main music directory on the external and allowed iTunes to automatically manage files or whatever it does.  I added everything and all was good.

I then rebooted into Ibex and the external was mounted fine.  I turned on Amarok and set my collection under sqlite or mysql, whichever is the default that they recommend for people who don't know how to do the extra setup.  I updated collection and it was working perfectly.  At some point I tried to find some music that I knew was on the hard drive in amarok, and it didn't show up in the library, so I tried to just check the files manually.  I opened up the hard drive and it said there were 0 files and 0 folders on it, but only 750GB free.  I decided to restart comp into Vista to see if that would fix anything, and when I did that it ran some sort of check disc thing that 'deleted the index of' all my movies and music. Now in Vista the hard drive launches fine, but I can't actually open the hard drive.  Whenever I try to it says Access Denied or No Permission or some bs like that.  Also, it does not display memory usage in Vista.

I switched back to Ubuntu and now I can see my files again, but my music folder only has 5GB of music in it (as opposed to about 60GB).  All my videos are normal, and there is a new folder called found.000 with a bunch of other folders in it called dirxxxx.chk and filexxxx.chk where xxxx are numbers from 0000 to 0158ish.  In each of these numbered folders there are a few songs that are named in iPod format (like xycc), but this folder only contains 2GB of music.  The tricky thing is I have 150 GB of DVD, yet Ubuntu says I have 750GB free.  This is the correct amount if I had 60GB of music, but as of right now I only have about 7GB of music.  

Where the hell is it?  And how do I get it to work in Vista again?

Thanks.

---

### Post by evw2k on 2009-01-07
So I was watching a movie on it earlier, because all of those were still there.  When I was a bout 90% done with it, it would stop playing in vlc, and then I couldn't re-open it after that.  I closed the window and when I reopened it, all of the movies in my movie folder were gone.  I haven't run Amarok and didn't really do anything to make it do this.  It still says 750GB free though.

---

### Post by evw2k on 2009-01-07
Okay, so I've found out that the dirxxxx.chk folders are actually a result of microsoft's chkdsk utility that was running automatically after I switched from Ubuntu to Vista.  I have tried messing around with permissions but I still can't access the hard drive in Vista.   The instruction manual suggests formatting the drive, which I really don't want to do.  I think I will back up onto a friend's external and then format it.  How do I make this not happen ever again?

---

### Post by evw2k on 2009-01-12
Okay, I know its been a while, but I still haven't gotten any help on this.  I have since backed up an image of my drive using Acronis.  After that I formatted the drive and moved what I could salvage from the image backup back onto the hdd.  Everything seemed to be working okay after that, until I tried to use it in Ubuntu again.  When I tried to mount the drive in Ubuntu I got the same error message as before about the mftmirr not matching the mft.

I found a thread [here]("http://ubuntuforums.org/showthread.php?t=656025&page=2")  that explains a method of solving this problem by going back into vista and just remounting it.  This method did not work for me because Vista could no longer access the drive, just like before.  So, I went back into Ubuntu and tried to do the ntfsfix thing that sneakywho_am_i described.  It sort of worked for the first step, but the second step totally messed it up.  Now I never even get error messages in Ubuntu when I try to mount the drive.  In fact, the drive does not appear in the GUI at all.  When i run fdisk -l it appears as normal.

In Vista, the drive still appears in the GUI, but it can not be opened.  The new error just states that windows can not access the drive because it is corrupted.  In computer management it still appears but it thinks it is in RAW format instead of NTFS format.  I can not run a chckdsk because Vista can not access the disk.  Also, in Acronis I can not make a backup of the drive because it is corrupted.  In Acronis it appears as NTFS but it says I'm using the entire disk, rather than just 150GB or so.  I literally can not do anything right now.  Please help.

---

