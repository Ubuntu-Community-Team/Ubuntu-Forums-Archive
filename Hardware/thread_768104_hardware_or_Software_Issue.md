---
title: "hardware or Software Issue?"
date: 2008-04-26
forum: Hardware
---

### Post by llanitedave on 2008-04-26
I've been using Kubuntu 7.10 quite happily since its initial release, until today.  Now, when I boot the computer, it goes through most of the initial setup, and then hangs right at the step "starting common unix printing system daemon (cupsd)."  There's no "OK" at that line, just a blinking period that will blink all day.

I *was* able to boot into the recovery console mode, but unfortunately I don't know how to track down the problem from that end.  I did copy my home folder to my second hard drive, so I have a backup.

Thinking it might be corrupted software, I downloaded (fortunately my wife has a computer of her own) the latest 8.04 version, and built an install disk.  I booted from the disk, and ran it through the disk check -- no errors.  However, when I tried to have it run Ubuntu from the disk, it got most of the way loaded, and then quit with a disk error.

Trying to install from the same CD, it got the kernel about 90% loaded (judging from the status bar) and then simply hung, becoming totally static and unresponsive.

My gut feeling is telling me that this may be a hardware problem, since it seems to be stalling in roughly the same place on both the installed system and the new cd.  Any suggestions on how I verify this?  

I'm going to disconnect my video card tomorrow and see if it will boot from the video on the motherboard.  Anybody ever had anything similar occur, and what was the solution?

Thanks!

---

### Post by llanitedave on 2008-04-26
Problem solved -- I guess you could call it hardware.  I removed all of the pci cards, and cleaned and vacuumed out the inside of the case.  (I've seen it dustier, but just making sure).  Then I reinserted the video card only, and rebooted.  It worked fine!  I've also replaced the wireless networking card, but I'm leaving the audio and modem cards out, since I never use them (onboard audio is plenty).

I'm now installing 8.04.  It's looking good!  Keep those connections clean, folks!

---

