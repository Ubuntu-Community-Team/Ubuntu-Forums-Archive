---
title: "Install Problems (Round 3)"
date: 2005-11-06
forum: General Help
---

### Post by groundpounder on 2005-11-06
A few weeks ago, I was trying to get Warty, and then Hoary installed on an older Compaq (hopefully the last one I'll ever work on), without any success.  I posted threads on here, but noone was able to help ( other thread is here: [http://ubuntuforums.org/showthread.php?t=72479](http://ubuntuforums.org/showthread.php?t=72479) ).  I set it aside, but now I want to try again.  I downloaded Breezy and attempted to install it today.  It looked promising, as it did get further in the boot process than Warty/Hoary, but alas, it still failed to boot.  Instead of a kernel panic, this time it displayed the following:

> ALERT! /dev/hdb1 does not exist. Dropping to a shell!

BusyBox v1.0-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off.

I find it rather paculiar that all of a sudden the hard drive doesn't exist after the installer had no problem recognizing it.  This happened on the initial boot after the install was complete, i.e. just after it spit out the cd.  I did just realize that the hdd is actually the primary slave, not the master.  I don't know if that's a problem or not (there is no primary master, that's the only hdd).  Please help!  I really want to get this thing working and out of my sight!  :)

---

### Post by trash on 2005-11-06
Well since you have had Warty installed before, i'm gonna guess this is a minor issue, have you changed anything in the bios since the good install? Have you changed any hardware cables since? When you install do you delete all the old partitions and use the auto patrtitioner to set up root and swap?

---

### Post by groundpounder on 2005-11-06
[QUOTE=trash]Well since you have had Warty installed before, i'm gonna guess this is a minor issue, have you changed anything in the bios since the good install? Have you changed any hardware cables since? When you install do you delete all the old partitions and use the auto patrtitioner to set up root and swap?[/QUOTE]

Thanks for the reply.  No, I haven't changed anything.  The bios editor is pretty much useless, There isn't even a place to change the boot sequence.  To get it to boot from the cd, I have to unplug the ribbon cable from the hdd, then plug it back in after it starts to boot from the cd, and yes, I made damn sure the cable was fully seated when I plugged it back in.  I let the auto partitioner take care of deleting the old and creating the new partitions, which it doesn't seem to have a problem with.  In fact, the install portion goes very smoothly, it's just when it comes time to actually boot from the hdd that the problems start.

---

### Post by trash on 2005-11-06
Cool that worked! But I wonder if that might be the reason why it's saying there is no hdd... if you have a floppy drive you should use a boot manager:

[http://ubuntuforums.org/showthread.php?t=81280](http://ubuntuforums.org/showthread.php?t=81280)

---

