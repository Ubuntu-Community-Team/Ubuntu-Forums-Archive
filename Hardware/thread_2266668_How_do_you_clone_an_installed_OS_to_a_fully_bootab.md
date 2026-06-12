---
title: "How do you clone an installed OS to a fully bootable DVD?"
date: 2015-02-24
forum: Hardware
---

### Post by NathanJoSharp on 2015-02-24
I installed Ubuntu to a flash drive, and its running great. In fact I made this post while running it.  However, I would like to copy the OS, and all the configurations on it, to a fully bootable DVD. I tried doing a google search, but most of the information is just on burning the Ubuntu iso and running Live CD. This isn't what I want, because I want to be able to have all the programs and settings of a fully installed OS but accessible through a DVD. I'm thinking of just running my OS like this and burning a new, updated DVD every 2 months or so. 

I tried copying the flash drive through dd to an iso image, but when I burned the iso, the computer didn't recognize it, at bootup or even on the desktop. 

> dd if=/dev/sdb[path of flashdrive] of=[/output filepath/filename.iso]

I would post the thread that I got this shell command from, but I can't find it now

---

### Post by weatherman2 on 2015-02-24
You can't do this, at least not in any practical way.  And why would you want to?  Flash drives are cheap - much faster than a DVD, more reliable.  8GB flash drives can be had for under $10 USD, sometimes for under $5 USD.

---

### Post by NathanJoSharp on 2015-02-24
I wanted to do this, because it eliminates any chance of getting viruses or malware. Potentially, it could be more secure too, for online banking (well that's of course if I regularly burn new disks to meet important security updates). Mostly, I wanna do it for fun though. I want it to run like a live disk but with my choice of programs and updates added in.

---

### Post by weatherman2 on 2015-02-24
If you're doing it "for fun" you can try something like this to make your own live CD:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

But if your goal is to boot from a "clean" image of Ubuntu each time, then update that image from time to time, there are easier/more practical ways to do it than trying to use a DVD.   The simplest way I can think of is to install Ubuntu in a virtual machine.  Then make snapshots of the image; you can always revert to the last saved snapshot each time you start it up, then update it once in a while if you want to.

I can imagine some sort of rig-up where you save an image of your / partition into a big file, then restore it on boot somehow - but that's a lot more work than using Virtualbox which already has snapshot capability built in.  I guess it depends how involved you want to get in re-inventing the wheel.

Look at LVM if you want to have Ubuntu partitions running "live" that you can clone while they are running - can't do it reliably without snapshot capability, which you can do with LVM but not with a regular partition.

---

