---
title: "Uninstall Ubuntu/Reinstall XP/hal.dll missing/boot.ini"
date: 2008-08-29
forum: General Help
---

### Post by fiddler616 on 2008-08-29
Hello,
When I boot up, I get GRUB which has the choice of Ubuntu/Windows XP. I can select Ubuntu, and it boots up perfectly.
However, when I pick Windows XP (these things happen...) it says something like:
<system-root>\system32\hal.dll
hal.dll is either missing or corrupted
Please re-install it

Hal.dll is not missing, and getting a new one didn't help.
Research has led me to believe that my boot.ini is messed up.
It used to say:
...partition(3)...
But since NTFS is on /dev/sda3, and Linux counts from 0 and Windows counts from 1, I changed it to
partition(4) [3+1]
No luck. Then I went into GParted, and I have the following partitions: (the order's important)
Windows | D drive (overflow Windows files) | Ubuntu | Swap
It used to be in a different order, but I reinstalled Ubuntu, and  used the time to put Windows first since another guy claims that having partitions in front of Windows makes it "push its toys out of the pram".
Same error.
Since Windows is first, I decided to try
partition(1) in boot.ini
No luck.
Before I get a string of links:
**I do not have a Windows CD, nor do I have any cool friends I can borrow one off of** though I do have the product key on the bottom of my laptop.
I have some semblance of a plan, which is:
back up important Ubuntu stuff
back up important Windows stuff
get Windows CD (see below)
Install Windows, and let it run rampant over the entire hard drive
Either install Ubuntu, or wait for Intrepid, or wait until I get the not-quite-as-important-as-this-one computer and can do what I want with it, with no fear.
I've gotten an inkling from my extensive Googling that it's possible/legal to download/burn the iso of a Windows disk, but I haven't been able to find a download.
So the questions are:
Am I on the right track?
Is there a much easier way of doing this?
Where can I, in fact, get a Windows XP Home iso?
You guys are all really smart/helpful, I'm sure I'm missing something important...I'll be F5ing this thread like no other (well, that's not true, I'll be watching my GMail for the notification like no other)
...I wasn't sure whether this belongs here (General Help) or on the other OS talk...
Thanks in advance

---

### Post by coffeecat on 2008-08-29
I have very little to offer you since you don't have a Windows CD. Just two comments:

> **fiddler616 said:**
> It used to say:
...partition(3)...
But since NTFS is on /dev/sda3, and Linux counts from 0 and Windows counts from 1, I changed it to
partition(4) [3+1]
No luck. Then I went into GParted, and I have the following partitions: (the order's important)
Windows | D drive (overflow Windows files) | Ubuntu | Swap
It used to be in a different order, but I reinstalled Ubuntu, and  used the time to put Windows first since another guy claims that having partitions in front of Windows makes it "push its toys out of the pram".

I can't quite follow what you did with the partitions, but I guess that is where the boot.ini problem has arisen. I'm afraid the guy who told you that Windows won't tolerate a Linux partition in front of it was - ahem - mistaken. I have Windows XP on sda2 on my Sony laptop - that's the way it came with a hidden partition on partition #1 (sda1 in Linux-speak). That partition 1 is now an (unhidden) ext3 one with PCLinuxOS, Windows still on sda2 and Ubuntu on a logical partition somewhere in the sda7-8 range. PCLinuxOS, Windows and Ubuntu (and a few other distros) all boot up quite happily, and I haven't seen any toys strewn about the place recently.

My only other suggestion is to use the 'Report' button against your own post to request a mod to move this to 'Windows Discussions'. You're more likely to get a response from someone with Windows knowledge there.

---

### Post by fiddler616 on 2008-08-29
boot.ini looks something like this (note: this isn't mine, it's the first thing I found on Google. If you want mine I can provide it)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect

so where it says default=multi(0)disk(0) etcetera, I changed the partition part. And did the same thing two lines down.

I'm glad that Windows isn't that temperemtal with the toys in its pram. Once I find the forum again I'll reread it, and then link to here.

Move requested.

Thanks you

---

