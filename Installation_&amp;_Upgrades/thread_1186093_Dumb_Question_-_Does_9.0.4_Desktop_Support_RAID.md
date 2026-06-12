---
title: "Dumb Question - Does 9.0.4 Desktop Support RAID?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by SedaliaSteve on 2009-06-13
I'm rather new to Ubuntu and haven't seen this answered. I'm setting up a computer right now that has two drives meant to be a RAID 1. I looked up how to set it up and there was discussion of how to choose RAID during manual configuration of the disks.

I just installed the 9.0.4 desktop and it gave me no options for RAID. I'm noticing the ubuntu.com mentions of RAID are on the server side. I really want the desktop. I just want to use a RAID to have some easy way to recover from a hard disk failure. Did I miss something?

If I burn all my music onto this box, I'd sure hate to have to do it again.

Steve

---

### Post by iponeverything on 2009-06-13
> **SedaliaSteve said:**
> I'm rather new to Ubuntu and haven't seen this answered. I'm setting up a computer right now that has two drives meant to be a RAID 1. I looked up how to set it up and there was discussion of how to choose RAID during manual configuration of the disks.

I just installed the 9.0.4 desktop and it gave me no options for RAID. I'm noticing the ubuntu.com mentions of RAID are on the server side. I really want the desktop. I just want to use a RAID to have some easy way to recover from a hard disk failure. Did I miss something?

If I burn all my music onto this box, I'd sure hate to have to do it again.

Steve

I am not sure if this is the right route for you, but I think alternate install CD will provide the options.

---

### Post by jerrrys on 2009-06-13
alternate install cd will work with raid, but you should consider a backup system.  raid 1 will give you backup only if hdd fails.  if you lose a hdd to software failure, you lose both drives...

---

### Post by iponeverything on 2009-06-13
NILFS sounds pretty cool.

---

### Post by moe19790 on 2009-06-13
> **jerrrys said:**
> alternate install cd will work with raid, but you should consider a backup system.  raid 1 will give you backup only if hdd fails.  if you lose a hdd to software failure, you lose both drives...


any way around this? suggestions?

---

### Post by SedaliaSteve on 2009-06-13
> **jerrrys said:**
> alternate install cd will work with raid, but you should consider a backup system.  raid 1 will give you backup only if hdd fails.  if you lose a hdd to software failure, you lose both drives...

How often do these failure happen with Ubuntu? Windows is prone to this with all the malware and its general instability. I will have a firewall and so far Ubuntu isn't getting much malware aimed at it.

The older UNIX systems were very prone to losing file systems when being improperly shut down. I've noticed over the years that all the UNIX flavors were getting better at dealing with this.

There is always sudden attacks of unintelligence by the user (me). Overuse of 'sudo' to run commands could clobber something through a typo.

I am downloading the alternate install CD to see how that works.

Steve

---

### Post by jerrrys on 2009-06-13
should work just fine...

[http://www.google.com/search?q=alternate+install+CD+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=alternate+install+CD+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by SedaliaSteve on 2009-06-14
It is fine now. I really screwed it up at first and it was a nightmare to fix it. I followed this [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")

I seemed to follow all the instructions and the install went fine but it failed to boot from the disk. I went through the install again and what had been the second multidisk device was now md0_raid1. It is just swap.

When I try to delete it I get an error: 'Failed to delete multidisk device'.'There was an error deleting the multidisk device. It may be in use.' It just wouldn't go away after attempt after attempt and many, many reboots. I finally tried an install as OEM. It still was difficult but eventually worked. When I redid it I was very careful to make sure it was correct. I think I fat fingered it the first time and crossed the root and swap RAID's.

I'm happy now. I have nice RAID system that I can start filling up.

Steve

---

