---
title: "BIG file problem, need the best!"
date: 2008-08-30
forum: General Help
---

### Post by mCion on 2008-08-30
Hi.

I had W. vista on my laptop, and then installed Ubuntu.  I wanted to stay with Ubuntu but had to keep vista cause ubuntu had trouble with my wifi.

ANYWAY, here's the thing:

Vista died.  totally, could not even get it started.  Before it died Vista was giving me bluescreens every 5 minutes(WHAT A SURPRISE!!!! XP).  I thought it was a HD problem.  So in the end I could not even open Vista

so I went into ubuntu, got the important files from the vista NTFS partition and using ubuntu copied them to my flash drive that uses a FAT32 file system.

Then I used a DVD that came with my laptop to reinstall Vista and all drivers and leave my pc as good as new.  When that was done the Bootloader didnt work anymore, so I couldnt get into my Ubuntu OS.

Since I still got a few blue screens, I ran all HD recovery and test programs that came with windows.  I also fused my old linux partition with my NTFS partition (since I could not access it and I didnt have anything too important there).  BINGO!!!, no more blue screens

SO!!!!!< HERE IS THE PROBLEM.
when I put my flash drive and look for my important files I mentioned at the begining, Windows only recognizes the files on my flash drive that where put in there by Windows (long time before all this), and not one of my important files put in using Ubuntu.  Vista doesn't even show them, it just shows free space.

ANY IDEAS ANYONE??

Ive tried Disk internal software and no success.  One program, Linux recovery gets half-way scanning my flash drive and crashes.

I'd like to secure those files before going in and reinstaling Linux.

THANKS!!!

>more specifications in case anyone needs em
I used Ubuntu 7.04
Windows vista 32 bit home basic
My flash drive is actually a Sony Walkman with 1 gb of capacity.  about 500 mbs are the files Im trying to recover.  Those files appear in windows as......free space.  My walkman has 300 mb of music put in there by windows.

---

### Post by monkeyking on 2008-08-31
Before trying to fix it, do a total copy of the drive.
Then try copying everything from the drive with dd.

Then I would do a physical check of the drive.

And then I would try various recovery programs.

---

### Post by Taxman415a on 2008-08-31
Try looking at it with when booting from an Ubuntu livecd. The you can see if you see the files. If not, use something like ddrescue (install with aptitude or synaptic, etc) to image the drive, then do your file recovery from that image.

For file recovery tools install the software listed here: [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software) again with aptitude, etc and read their manual pages.

Another good file recovery resource is here:
[http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254](http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254)
it describes the background on using some of the above tools.

---

### Post by mCion on 2008-09-01
thnx guys, I'll look into it tomorrow (now its too late) and keep you posted

---

### Post by Jouke74 on 2008-09-01
You did unmount the drive before you took it out did you??? Otherwise you might be in more trouble.

---

