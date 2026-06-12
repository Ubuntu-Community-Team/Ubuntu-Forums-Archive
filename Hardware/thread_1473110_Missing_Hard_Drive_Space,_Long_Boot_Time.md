---
title: "Missing Hard Drive Space, Long Boot Time"
date: 2010-05-04
forum: Hardware
---

### Post by orlok on 2010-05-04
Hey all, I haven't posted much, but I use the forums extensively when I encounter problems.  I finally have to post a seemingly complicated issue.  I've probably compounded the problem trying to fix it myself.  So here it goes.

I have an EEE PC 901 running Ubuntu 9.10 (and I love it!)

Over time, I encountered more frequent crashes--downloading big files in Transmission prevented my laptop from shutting down, so I'd have to hard reset, which led to lots of fsck-ing.

I installed Ubuntu Tweak and it seems like the problem was exacerbated.  

Recently, my computer failed to boot up, unless I tried a bunch, or waited for a day or so to try again.  

Now, the load time takes forever.  If I hit [Tab] when it's booting, the BIOS boot screen sits at "Auto-Detecting Sec Master.." for a couple of minutes before finally booting.  I 'dealt' with this problem, discovering that UUIDs for my swap space and for /home weren't working--so I changed them to /sda1 and I was finally able to boot to the log-in screen.  Then the XAuthority permissions didn't work, so I used the terminal to just get rid of it, since it automatically generates new permissions.  

Success!  Sort of.  I am able to log in now.  But now about 7-8GB of HD space is absolutely missing.  I'm not sure where it went, nor how to find it.  I also can't get my USB thumb drive to be detected.. or I'd just put 10.04 on it and call it good (making a thumb drive on my roommate's mac sucks, by the way!)

I know this is kind of long-winded.  I don't know where to start.  Any help is much appreciated!

---

### Post by SnickerSnack on 2010-05-04
1. Get it to boot.
2. Backup important files.
3. Reinstall.

That's probably the easiest and fastest way to fix it.  It sounds like there is probably more than one problem.

I don't know how hard it is get the hard disk out of a netbook, but if you can't get it to run long enough to backup files, you can take it out and connect to a working machine to make the backup.

The fact that 7-8 GB of space seem to be missing suggest to me that you need to format and repartition the hard drive.  How old is the hard drive?  Edit: What exactly do you mean by "missing"?  Does the whole drive appear to be smaller than it used to, or do you simply have less free space than before?

---

### Post by orlok on 2010-05-05
Sorry, I was really tired last night.

The whole 16GB SSD is missing.  So I've got the 4GB drive that's solder'd to the motherboard detecting, but the other one is not.

And by missing, I mean it isn't appearing in linux or in the recovery console (but I'm not sure how to check exactly.)  It's physically present in my computer.

I can boot, but I guess I need to make a thumb drive on a different computer--I don't have the space to download the .iso.

Any other suggestions before I just master blaster this thing?

---

### Post by orlok on 2010-05-06
An update:

I've mentioned before that I figured out that my entire 16GB SSD vanished.  I'm not sure how this happened--whether it was my fault, or it's toast, or a combination of both.

I was able to properly format my thumb drive after much difficulty on an XP machine with Ubuntu 10.04 NBR.  However, my thumb drive is not booting as a live disk at start-up.  My BIOS is set properly for this to work, so I'm not sure what the problem is.

Would a good next step be flashing the newest BIOS on to my computer?
Also, I am going to try removing the SSD drive and reinstalling it.  If that fails, I am going to remove the drive and start up the machine to see if it gets rid of the slow boot time (where it appears to be trying to read that SSD, which may be the mysterious "Sec Master".)

Any suggestions would be great!

[EDIT]
I just tried starting up without the SSD and encountered no problems with boot time.  I suspect that USB might work now too?  We'll see.  
Is there a way to check to see if a drive is totaly busted?  Or if it's repairable?

---

