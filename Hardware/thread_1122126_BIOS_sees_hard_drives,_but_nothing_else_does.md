---
title: "BIOS sees hard drives, but nothing else does"
date: 2009-04-10
forum: Hardware
---

### Post by dougmurphy34 on 2009-04-10
In an effort to convert from Windows guy to Linux guy, I built a new machine. Everything looks good except that, while the BIOS sees and recognizes my sata hard drives, no operating system seems to.  My IDE CD drive seems to work fine.  I'm losing my mind here and would love some help.

HARDWARE SPECS (all brand new from newegg):
Intel Core 2 quad
EVGA nForce 780i SLI FTW board
Western Digital WD6401AALS sata hard drive
GSkill RAM 2x2GB

TEST RESULTS
1) Ubuntu 64-bit desktop: downloaded ISO.  Ran without installing (from CD); was able to open spreadsheet, browse in Firefox, etc.  Tried to install from desktop icon.  Got as far as partition choices; could not find any hard drives.  Rebooted and tried to install directly (option 2 from the initial menu); hung up looking for sata.  

2) Kalyway 10.5.2 - Several times, failed to load at all, hanging while looking for sata.  Once, loaded to GUI, but when it asked me what drive to install to, it didn't see any.

3) Known good drive - plugged in my 250GB Western Digital sata drive from my old machine, runs Windows XP.  Showed up in BIOS but not recognized by Ubuntu.  Tried to boot from this Windows drive, got "Master Boot Record Error".  Put back in old machine (store-bought HP); worked fine.

I have tried: moving drives to different SATA sockets on the motherboard, one sata drive at a time, two at a time.  I'm not sure what to try next.  This post:

[http://ubuntuforums.org/showthread.php?t=674882](http://ubuntuforums.org/showthread.php?t=674882)

seems to say that my motherboard is supported by Ubuntu, which should imply that my sata controller is supported.  Is there anything else I can try?

Any help appreciated.

Doug

---

### Post by dougmurphy34 on 2009-04-10
The saga continues.  I got a Windows SATA drive to work, but it wants me to activate (as if I hadn't been using this copy of Windows for two years)and it can't find my NIC.  So back to the old drive, Kalyway decides it can see my drives, I partition the 650GB and and I had Kalyway 99% loaded on 1st partition when it froze, then it booted halfway in Darwin and froze.

So, back to Ubuntu I say, I've got a nice clean partition for it now.  Pop in Ubuntu disk, reboot . . . can't see SATA.  Won't even load the "run Ubuntu without installing" option anymore.  

I'm at a loss.  Anyone?

--Doug

---

### Post by dougmurphy34 on 2009-04-13
[FIXED]

Information Technology 101: First, check the cords.

I had a frayed SATA power cord.  Swapped it out, installed, looks gorgeous.  All better.

Of course, WOW won't run right, but that's a story for another thread.

Doug

---

