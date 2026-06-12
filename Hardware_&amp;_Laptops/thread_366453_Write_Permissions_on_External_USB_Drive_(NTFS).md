---
title: "Write Permissions on External USB Drive? (NTFS)"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by Matt Volatile on 2007-02-20
I've had great success in my first few hours of using Ubuntu... I'm so impressed with Edgy as so much seems to have worked first time compared to previous versions. I'm still not quite sure of what exactly the terminal commands I'm executing actually do but following code step-by-step is getting me places, fast! :)

I now know how all those people I helped out with Windows problems felt when I expressed incredulity at their problems - this must be karma catching up with me.

Anyway: I have a 300GB external Maxtor One-Touch USB hard drive (NTFS formatted), and it was auto-detected on installation. I can happily browse, execute and copy files from the drive. Obviously, though, I can't get write permissions to the drive and this is where I need to ask your help.

All the How-Tos for writing to NTFs partitions seem to presume an internal drive, and all the guides for external drives don't seem to touch specifically on how to obtain write permissions. Where should I start?

---

### Post by divague on 2007-02-21
This how to worked for me

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

> External device are automatically configure when plug

---

### Post by fsando on 2007-02-24
This did NOT work for me - any ideas?
On ubuntu 6.10.
Installed ntfs-3q through synaptics - rebooted. Have external usb w/3 ntfs partitions.
When attatched (ie insert usb cable) partitions shows up with little padlock-icons and are write protected.

---

### Post by givré on 2007-02-24
fsando, did you really follow [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) ?
Did you add my third party repo ? This is require in order to get write support on usb device.

---

### Post by fsando on 2007-02-26
> **givré said:**
> fsando, did you really follow [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) ?
Did you add my third party repo ? This is require in order to get write support on usb device. [redface] no I did not add the repo - anyway I've screwed my system in so many other ways I've lost track - I'm beginning to realize the truth in lnux-is-not-windows (don't recall the exact url). Many years of win-experience only gets you so far. Poking around is not too clever when you are in reality a noob. On the other hand - this is how I learned windows, starting from win 3.1. Trial and error - lots of trials, lots of errors ;D.
Thanks for your answer, I'll be more meticulous next time.

---

