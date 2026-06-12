---
title: "data coruption, multiple hard drives."
date: 2010-02-25
forum: Hardware
---

### Post by weirdtalk on 2010-02-25
So several weeks back I woke up and found my computer had froze. It didn't respond to alt+sysRq+k or reisub, so I rebooted and was given a error similar to "root partion not found, please run fsck manually" so I ran fsck and after a minute it had fixed the problem and I was back on my way.

A week later it happened again. And again fsck fixed the problem. This happened maybe twice more, before I noticed that several of my files had gone missing, (like my firefox setttings and a few docs, etc.). It wasn't a big problem because I had a external backup. But I was suspecting a bad install, so I formatted the drive and reinstalled ubuntu 9.10 with ext4.

The issue remained. So I formatted to 9.04 with ext 3. The issue remained.

I now suspected the hard disk. So I swapped my 1TB drive for a 40GB drive (and a new install) and zeroed the 1TB and got ready to ship it back to the manufactur. 

A day later the computer would crash at random and would restart X. When I rebooted it had to run fsck manually.

I began to doubt that it was a hard drive problem. So I enabled smart on both drives (40GB ide and 1TB sata) and ran the long diagnosic, it found no errors.


So what is going on?

---

### Post by weirdtalk on 2010-02-28
So it happened again today. It partially crashed. The application bars disappeared. Terminal would only display every other character. When I tried to relaunch virtualbox (it was running when it crashed) it would display seg fault (well it displayed "s g f u t" and I gathered that what it was).

so I rebooted and I had to do a fsck on the 40 gb (I now have both plugged in).

So I got thinking maybe the crash is causeing the hdd problem instead of the other way around. I did a memtest but it didn't find anything.

What else could it be?

---

### Post by efflandt on 2010-02-28
Have you tried running memtest86+ for a few hours just to make sure you do not have memory issues or other system problems?  I remember that some time ago some system boards had capacitors that would leak.

Some one at work thought they had a hard drive problem when Windows would occasionally blue screen.  It still happened occasionally after hd was replaced.  Apparently the RAM that Crucial thought was compatible was not quite.  When I ran memtest86+ it came up with errors.  When I put the original RAM back in the PC it had no errors.  And the stick that had errors on that PC had no errors at all when installed on another PC.

I did try to recently use an old hard drive that apparently was failing.  Gparted would only let me partition about 35 GB + 2 GB swap on a 60 GB drive.  Any more that that and gparted could not recognize the partition type immediately after it formatted it.  Eventually I was somehow able to partition and format the rest of it.  But when that did not seem quite right, I tried to fsck it marking badblocks.  But I gave up after about 11 hours when it was constantly finding and marking badblocks.  So I retired that drive.

---

### Post by weirdtalk on 2010-03-01
I had run a single pass with memtest, but I will run it overnight to be sure. 

I also had another idea. I used the binary nvidia drivers on both 9.10 and 9.04 so maybe that's causing it.

I'll let you know.
-Thanks

---

### Post by weirdtalk on 2010-03-01
Well the memtest came back clean after 10 passes (~12 hours).

---

### Post by tgalati4 on 2010-03-02
Power supply could be failing.  Check the 12v leads with a voltmeter.

---

### Post by weirdtalk on 2010-03-09
yep it's 12v. 

Well I tried to switch to a open source driver, but I couldn't figure out how to get a resolution larger than 800x600. So I switched back.

And it crashed again today. I still had a partially working x. I could use the app menu, but it wouldn't launch games. The emergency shutdown didn't work, so I rebooted the machine. Once again it needed to fsck before it would boot.

How can I find out what is causing this? Are there some log files? Something else?

---

### Post by Fafler on 2010-03-09
Try underclocking your CPU. Does 9.04 and 9.10 come with the same kernel? Maybe try another distribution?

---

### Post by Choragos on 2010-03-09
Well bad memory can cause what you're describing, but memtest came back clean.  Can similar problems with a graphics card also cause hard drive issues?  I wouldn't think there's any back-and-forth writing, but maybe...

---

### Post by doas777 on 2010-03-09
i actually had an application crash in windows a few years ago that damaged the disk firmware or io controler. it was ugly. after spending a weekend trying to fix it, I ended up having to backup and get rid of the disk.

---

### Post by h6w on 2010-03-11
IME, this can also be from a faulty power supply.  Power supplies can be fine when you test them, but fail under load.   I would try replacing the power supply and see if it stays up.

The next thing (after discounting the memory and hard disk) would be the mainboard.  I've had plenty of disk controllers go wacky after a minor brownout.  

I've also currently got a new disk chassis on my desk that gave me multiple disk failures shortly after plugging it in.  Took it out of the loop and all the disks work perfectly.   If there's anything in between the disk and the mainboard, I'd take that out of the loop, too, and see if it makes a difference.

---

### Post by weirdtalk on 2010-03-28
I had decided to sleep on the issue for a while and clear my head. I came back and loaded sabayon on it just to try something different. Well I was playing around in the bios when I saw my cpu temps. It was running at 50c while idle. It seemed a little hot so I opened the case and looked at it. One of the pop rivets had come undone. I used my finger to push the heat sink down and watched the temp drop about 10c in a few seconds.

So I shut it down and re-attached the heat sink. Then installed ubuntu (so I had a clean linux again) and installed and ran mprime over night to be sure I had not blown a cpu. Luck was on my side, it was still running in the morning.

A easy fix to a hard to find problem.

Thanks everyone for your help.

---

