---
title: "Onboard ICH9 AHCI is too slow..."
date: 2009-02-06
forum: Hardware
---

### Post by Abzstrak on 2009-02-06
I can't figure this out and need a hand.  I have one Windows machine that is used for gaming, I've been running Linux for some time for real tasks.

I finally got fed up and decided to format my gaming rig and will use Cedega for my gaming needs.... I have two problems, one the extra 8600GT I have in the computer for PhysX really pissed off the nvidia drivers, so I pulled it out... not sure it ever really got used anyway.  The other is that my drives are WAY too slow.  

Motherboard GIGABYTE GA-X38-DS4
CPU : Q6600 @ 3.4GHz on 1700MHz FSB
RAM : 4GB OCZ 1066 @ 1133MHz
Video : 9800GX2
SATA Controller : ICH9R, I running it in AHCI mode though.
HDD1&2 (SATA1&2) : 2x 150GB Raptor's in RAID0 (linux software raid)
HDD3 (SATA3) : 250GB 7200rpm drive for windows if a game really needs it (right now its blank)
Optical1 : IDE1 Master
Optical2 : IDE1 Slave
Optical3 : SATA 4
OS : Ubuntu 8.10 x64 all updates and nvidia 180.11 drivers

when I do a hdparm -tT /dev/md1 I end up with results about like these:
Timing cached reads = 5000 MB/sec  (yes, this is pretty good)
Timing buffered disk reads = 35 MB/sec  (this is *** slow, I expect around 100MB/s at least)

I'm at work now so I cant give the exact results, but I played with it alot last night to no avail....  it always gets about 35MB/s on buffered reads which really sucks for two 10000rpm drive in a stripe.

I tried disabling AHCI, no help. I tried reinstalling using the Intel crap RAID, and the installer can't find it (yes I used the alternate install disk).  I figured I'd run Bonnie on it some tonight, but honestly I haven't had hdparm fail me at giving me halfway accurate results ever....  I think something is wrong, something needs changing, but I can't figure out what.  I do not know of any settings to change regarding this and I cannot find anything remotely similar through multiple searches.

Also, I did try clocking everything back to stock speeds, it didn't change the speed of the drive according to hdparm.

please help any ideas are appreciated.

---

### Post by theEarl on 2011-08-06
I am suffering from the same problem and I was wondering if you found a solution or at least an explanation to why this is happening?

In Windows 7 I see speeds of 70-100MB which are in steep contrast to the 30MB read speed I achieve in Ubuntu/Mint.

---

