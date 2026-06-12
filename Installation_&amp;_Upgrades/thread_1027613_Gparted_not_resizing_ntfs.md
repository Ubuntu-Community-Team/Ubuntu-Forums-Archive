---
title: "Gparted not resizing ntfs"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by smarticals-and-cheese on 2009-01-01
I have been trying to dual boot windows and ubuntu intrepid ibex.

When i open gparted to resize my ntfs partition (which uses up most my harddrive)

it doesn't seem to work. I have no other partitions and i have 8mb of unallocated space and 256 mb of an unknown file system.

when i double clicked on my ntfs partition fro more info i found the following


[I]ERROR: This software has detected that the disk has at least 1 bad sector
*************************************************************************
*WARNING: This disk has a bad sector. This means physical damage on the disk*
*surface caused by deterioration, manufacturing faults or other reasons*
*The reliability of the disk may stay stable or degrade fast. We suguest*
*making a full backup urgently by running 'ntfsclone --rescue ...' then*
*run 'chkdsk /f /r' on Windows and reboot it TWICE! Then you can resize*
*NTFS safely by additionally using the --bad-sectors opetion of ntfsresize*
**************************************************************************

Unable to read the contents of this filesystem!
Because f this some operations may be unavailable.[/I]

I dont really have any idea of what this means so can anyone help
and when i used

ntfsclone --rescue /dev/sda1 --ouput /dev/sda4

in Terminal, i got

ubuntu@ubuntu:~$ ntfsclone --rescue /dev/sda1 --output /dev/sda4
ntfsclone v2.0.0 (libntfs 10:0:0)
_**ERROR(13): Opening '/dev/sda1' as NTFS failed: Permission denied**_
ubuntu@ubuntu:~$ 


Please, someone help me =(

---

### Post by logos34 on 2009-01-01
If it's XP, boot from your windows install cd and go into Revcovery Console.  At the prompt run

chkdsk /r

---

### Post by smarticals-and-cheese on 2009-01-02
> **logos34 said:**
> If it's XP, boot from your windows install cd and go into Revcovery Console.  At the prompt run

chkdsk /r

what if you don't have the install cd anymore?
(and yes, i do use XP)

---

### Post by taurus on 2009-01-02
Boot into windows and defrag your harddrive a couple of times.

---

### Post by logos34 on 2009-01-02
I misread your post--if it's just mounting you're having problems with but can still boot into windows, do so and run error checking w/repair option.  And defrag as just suggested.
You would need to use the cd, however, if you can't boot windows

---

### Post by Mike.lifeguard on 2009-04-08
I'm getting the same error. I've run chkdsk /f /r from within Windows and rebooted, but still Gparted tells me the disc has bad sectors. However, apparently ntfsresize --bad-sectors can safely resize the partition now?

I've defragged fairly aggressively & will be shortly removing Windows' pagefile. Anything else worth doing?

I'm trying to resize (shrink) my WinXP partition to make room for Intrepid (dual-boot) too.

---

### Post by Mike.lifeguard on 2009-04-10
See [https://lists.ubuntu.com/archives/ubuntu-users/2009-April/180136.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-April/180136.html) (& possibly my previous posts in that thread) for my solution here.

---

### Post by Herman on 2009-04-10
I think that anyone who has a hard disk with badblocks should back up all their data immediatley and start shopping for a replacement hard disk right away.

Some people might have data that's worth a lot of money, hundreds or thousands of times the price of a new hard disk.
Other people might have data that they put a lot of work into, or that has sentimental value and may not be able to be replaced.

Data on a hard disk is stored as combinations of tiny positive and negative magnetic fields or flux. 
Bad blocks are sectors in the hard disk that are losing their magnetic properties to such an extent that they can no longer be trusted to store data reliably.

New hard disks have some bad blocks and they also have an area of spare sectors that the hard disk's controller will silently swap for the bad ones. Gradually more bad blocks will appear from time to time as the hard disk ages, and those are also silently swapped for spare ones by the hard disk controller.

Only after the hard disk's supply of spare sectors runs out, do bad blocks begin to become apparent to programs like fsck or the badblocks program.
When that starts to happen you may be able keep it going a little longer by running programs like fsck repeatedly, but fsck doesn't 'fix' bad blocks, it just maps them out, (tells the file system where they are so it can work around them).

It's anybody's guess how much longer a hard disk like that will last. That depends on what problem is causing the bad blocks.
If it's an old hard disk, it might have reached the end of it's natural working life and be due for retirement.
It's probably okay to keep using it for a while as long as you don't care about storing any important data on it.
You can use it for trying out operating systems, but don't complain if the operating systems you are testing perform poorly and have all kinds of bizarre problems.
Regardless of whether the hard disk is old or new, there might be a mechanical problem of some kind developing. 
Maybe the spindle bearing is about to collapse. If that's the problem it will most likely degenerate rapidly. 
If you don't back up all your data right now, you may not get another chance!

Since most users have no way to tell for sure exactly what might be wrong with their hard disk, continuing to use any hard disk with bad blocks is a big risk. Really, you are probably wasting your time and risking your data. You should definitely start looking for a better hard disk.
If you can't afford to go and buy one, often if you ask around you can even find one that's in good condition for free from somewhere, maybe from someone who has upgraded to a larger capacity hard disk and doesn't have the physical space in their box for their low capacity used hard disk.

I don't want to sound like a cranky old troll, but I strongly feel that people need to be warned.

Regards, Herman :)

EDIT: If it's the first time the hard disk has had any badblocks and there's only one or two you still might be okay, it might be just a new one that the hard disk controller hasn't had a chance to swap out yet. But keep an eye on it. (Run the Linux 'badblocks' command in Ubuntu fairly often,
[FONT=Bitstream Vera Sans Mono]```
sudo badblocks -sv /dev/sda2 >> badblocks.report
```[/FONT] (Tests partition number 2 for badblocks and writes the ouput to a file. When you go and read the file it should be blank and empty if the hard drive has passed, (it didn't have any bad blocks).
Feel free to replace the '/dev/sda2' with any other partition number.
The badblocks test can take some time, that's why it's best to run it in one partition at a time rather than an entire hard disk at once.

---

