---
title: "Karmic Install Fails: [Errno 30] Read-only file system"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by AgentWD-40 on 2009-11-02
I've been looking for a solution to this problem all morning, but I haven't been able to find anything. I was running Jaunty on my laptop and decided to wipe it out and do a clean install of Karmic. I first booted using the live CD and everything worked great. When I try to install it, I get the message below at the 38% mark. I checked the CD for errors and no errors were reported. Any ideas about what's going on? Thanks in advance for your help!

The installer encountered an error copying files to the hard disk:

[Errno 30] Read-only file system

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

---

### Post by AgentWD-40 on 2009-11-05
I have since solved this problem. :D

I downloaded a new copy of the ISO and burned a new CD. The install failed on errno 30 again. I tried creating a USB start up disk instead and that failed on errno 5. Just when I thought things weren't going to work out I decided to break my disk mirroring RAID set up and install to just one of the drives using a CD, then rebuild the array. It then installed perfectly and I was able to re-create and rebuild the array. I'm quite impressed with Karmic so far! :D

---

