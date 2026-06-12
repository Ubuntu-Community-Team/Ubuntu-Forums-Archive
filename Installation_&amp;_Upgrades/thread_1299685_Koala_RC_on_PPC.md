---
title: "Koala RC on PPC"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by omgseth on 2009-10-24
I've tried using both the LiveCD and the Alternative disc and both hang at 0% when it tries to format. Any ideas? I've tried many times but nothing seems to work. I'm installing on a Mac PowerBook G4.

---

### Post by motsteve on 2009-10-24
Do you know how to partition manually?  Can you use your PPC to format using mac-disk from another Linux partition ?  It may just need a little helping hand.  Are you using the install and it never gets to the partitioning portion of the installer where you can use the entire disk or partition manually?  I don't have my DA anymore, so I'm going on memory for installation, but I did so many I might be able to help with a little jogging.

---

### Post by omgseth on 2009-10-24
I did the partitioning manually and automatically and both times after I confirmed the changes to be made the installation would start and it would say "formatting swap hda1" or "formatting ext4 hda1" or whatever, but the bar wouldn't move, just sits there at zero :\ Oddly, Jaunty installs fine.

---

### Post by omgseth on 2009-10-25
I thought about maybe just installing Jaunty then upgrading, but a fresh install just sounds better ( cleaner, faster, etc. ).

---

### Post by motsteve on 2009-10-25
Don't feel like the Lone Ranger here.  I can't upgrade my 64 bit Jaunty to Karmic on my i7 box.  I just went back to Jaunty and am happy here until the Karmic version gets a little more stable.  If you are like me and an avid techie, you're probably antsie and want to get into the new action, but it looks like we're both SOL until the new stuff comes out a little further on down the road. ;-)

---

### Post by Topsiho on 2009-10-25
> **omgseth said:**
>  Oddly, Jaunty installs fine.

I had exactly this same problem on my test computer, the other day.
Karmic refused to install, Jaunty installed fine (and after that did not boot).

Karmic has a new tool, which is great, in my opinion: palimpsest, a disk utility that reads the disks S.M.A.R.T. data. It appears my disk was "prefail", and could not be trusted anymore.

This was also indicated in the righthand top of the screen, using the LiveCD.

I also noted that while booting, my HD was not recognized anymore by the BIOS.

So if you have this (these) same warning(s), that the disk is not OK, you'll not be able to install Karmic (and waste a lot of time, and being frustrated, doing so).

(with an other hard disk, Karmic RC is now up and running fine. This HD is considered healthy :)  )

S.M.A.R.T. is the capability of disks to compile statistics of their performances during their lifetimes.
Palimpsest reads and interprets these statistics. And it can do more than that, it's als a partition editor.

Topsiho

---

