---
title: "Hard crash on live CD &amp; installed system"
date: 2008-08-08
forum: General Help
---

### Post by thrice on 2008-08-08
I'm trying to install i386 Kubuntu 8.04.1 onto my Shuttle box, and it's crashing hard each time. The live CD boots from the CD, and X starts, but when the KDE desktop (KDE3) starts to come up the machine locks hard - no Caps lock light, no Alt-Sysrq. Hmmm...

I have 2 of these machines. One was installed with Gutsy and upgraded to Hardy, and that one is fine. The problematic one is currently running 64 bit SUSE-10.2 and its root filesystem is on a RAID1 array. That's the only hardware difference between the machines - 2 disks not one, /dev/md0 not a single SATA device.

As I said, I tried the standard CD and it reliably crashes the machine when the desktop is coming up. I downloaded the alternate install CD and tried that. No live CD option there so I did a complete install. It found the array, mounted it (I want to keep the contents) and installed correctly onto it. But the machine still crashes when KDE comes up - sometimes it crashes when KDM is coming up.

If I boot it into a terminal environment it works fine. From this I deduce that the raid array isn't the problem, although that's the only material difference in hardware. I updated everything but it made no difference.

I'm going to try Ubuntu tonight to see if that has the same problem (although I really want KDE, so I'm not sure if that will be a real solution). I'm also going to try (horrors) openSUSE 11, but that is the distro I really want to get away from! In the meantime, does anyone have any clue or suggestions?

---

