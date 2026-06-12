---
title: "old pc dual boot ibm"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by idiota on 2009-05-07
Hello everyone,
 
I'm trying to set up ubuntu from the minimal CD, dual-booting with WinXP on a 5 year old IBM PC. I have one physical disk, 37GB, with 4GB for the IBM recovery partition and the rest for XP.
 
I defragged and used the GParted iso CD to shrink the WinXP partition to half its size, then rebooted and confirmed Windoze was in good shape. Then I ran the minimal CD and told it to install to the largest available space. It set up swap and ext3 partitions, and GRUB, fine. WinXP remains good.
 
TWO PROBLEMS:
 
PROBLEM 1
 
F11 Recovery doesn't work - presumably because IBM have a custom MBR that Ubuntu has nuked. The IBM recovery partition IS visible in GRUB, and it boots into it ok - and then crashes. The display is:
"Setup is inspecting your hardward configuration"
"Press F6 if you want to install a SCSI or RAID 3rd party driver" (this works - so it HAS booted....)
"IBM Rescue and Recovery System" (blah)
"Please Wait"
Then blue screen STOP: c000021a The Session Manager Initialization process terminated unexpectedly with a status of 0x000003a (0x00000000 - 0x000000000). I found in other forums via google that this is pretty much the utter death of windoze - people are talking about SAM password files, and the MS KB says winlogin or csrss has failed. 
 
I'm sorry if this is off-topic (the issue is that IBM's recovery partition is actually another - *drastically* customised - XP install) but why did ubuntu mess with that partition? I told it to use biggest available space - and it did.
 
PROBLEM 2
 
Ubuntu gets past the splash screen animation, then displays PC DISPLAY SETTINGS CORRECT? (with no buttons or Y/N) and then doesn't react to the keyboard. After a few seconds it locks into a black screen. The power button powers things down nicely, so obviously ubuntu is running and I have a display settings issue with this ancient monitor. I tried the recovery mode - it all looks nice until I resume normal boot, then the same thing happens. 
 
Could some kind person please point me to an article on configuring ubuntu for an old monitor from the command-line?
 
God bless y'all

---

### Post by dandnsmith on 2009-05-07
> I'm sorry if this is off-topic (the issue is that IBM's recovery partition is actually another - drastically customised - XP install) but why did ubuntu mess with that partition? I told it to use biggest available space - and it did.

The messing was, almost certainly, installing the grub loader. Other machines (not necessarily IBM) have reported similar problems - once clobbered it seems to be a trifle tricky to get back.
Do you actually want to be able to use the recovery feature? as it oftens seems only to work if you retain the original partitioning.

> PROBLEM 2

Ubuntu gets past the splash screen animation, then displays PC DISPLAY SETTINGS CORRECT? (with no buttons or Y/N) and then doesn't react to the keyboard. After a few seconds it locks into a black screen. The power button powers things down nicely, so obviously ubuntu is running and I have a display settings issue with this ancient monitor. I tried the recovery mode - it all looks nice until I resume normal boot, then the same thing happens.

I think you need to get to a terminal (from the CD, possibly) to try booting with 'safe' graphics. Have you tried a 'live CD' to see if the graphics work for that (one of my criteria for deciding whether to use a particular distro/release)

---

