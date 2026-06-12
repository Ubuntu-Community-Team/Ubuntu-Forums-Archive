---
title: "grub(?) problem on first boot"
date: 2005-11-14
forum: General Help
---

### Post by ttrygve on 2005-11-14
So, I'd been doing a lot of reinstalls (dozens) in the past few days, at first trying to get around an LVM problem I was having, but eventually trying to reproduce it so I'd know and be able to document for others exactly what had gone wrong, because at the time, I thought it was an issue created by using the partitioner in the installer to set up LVM.  I was eventually proven wrong, however, and led to believe that whatever had caused my problems (likely to remain a mystery at this point) was unrelated.

But on one of those test installs, I had all four of my hard drives plugged in, though I don't recall if I told the install to use all of them, and on first boot, simply got a flashing cursor.  I ended up reinstalling two or three more times (using variations on partition layout, file system type, an whether I used LVM or not), but kept getting the same flashing cursor.  Attempting to reboot again would still just result in a flashing cursor.  Eventually, I unplugged all but the first drive, and reinstalled to that, and the problem went away, and then (out of overcautiousness) I shut down, unplugged that drive, plugged in the other three, zeroed the beginnings of those disks with dd, then shut down and plugged in the first drive again, and was then able to boot with all four drives plugged in again.  Even on successive test installs, the problem did not return.

Until last night.  I was doing an install using a non-LVM'ed ext3 /boot, and the rest of the first disk as LVM, broken into several reiserfs partitions (and one swap).  The remaining three disks had been zeroed recently, so they didn't even have partition tables at this point.  I'm fairly certain I've done installs like this before without problem, but at this point they've all kind of blurred together.

But this time, having seen it once before, I immediately unplugged the other three drives, and was about to reinstall to the first again when it occurred to me to try booting off it as is first, and lo and behold, merely unplugging those three drives, and then rebooting, this time I finally saw grub load the kernel and get things started, and from there the first boot went completely normally.  After it had booted (and I ran the updates), I shut down, plugged the other three drives back in, and this time everything came up just fine!

I'm really baffled why having blank disks plugged in prevented the first boot from working, but worked just fine on the second boot.

At this point, I've given up trying to reproduce my original problem, I have my system installed the way I'd wanted it, and I'm finally starting to restore from backup, so I'm not really eager to keep experimenting to figure out why that happened.  But I am still very curious, can anybody think of a reason that might have happened?  The disks appear to be working just fine.  I ran "badblocks -vw" (a destructive write-read test making four passes over every block on the disk) on all four of them at one point during this process, and it found no problems.  I don't *think* it's a hardware issue, but at the same time, I can't think of why grub would've failed to load one time, and worked just fine the next.

Any ideas?  Or should I just forget it and move on?  =)  Thanks!

---

