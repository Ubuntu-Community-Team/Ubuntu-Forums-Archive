---
title: "Tweaking a Dual Boot of Windows and Ubuntu"
date: 2008-08-22
forum: General Help
---

### Post by SaikoRonin on 2008-08-22
I currently dual boot windows xp and ubuntu hardy heron.

I do not use the windows version as, unbelievably theres a video and sound driver problem on it.

I would like to have access too a few windows programs and files that are unavailable through crossover/wine

Is there a way to install a new windows over the windows partition without pulling out my ubuntu hard drive(I have the 2 hard drives seperated)

Or if there was a way to use windows within ubuntu for certain programs that would be the ultimate solution.

any ideas?

---

### Post by the_softy on 2008-08-22
It is possible to run windows when booted in ubuntu. You have to use a program like VMWare player or virtualbox. I'm new here, but I think there is a howto about virtualbox somewhere on the forum. 


You can also reinstall windows, just make sure you install it on the right disk.
Normally when you install windows it overrides the master boot record(mbr). I'm  not sure what will happen if you have 2 disks. But I think you can run a linux live cd and reinstall grub, which will create a menu so that you choose your OS at boot. You should search the forum. The answer should definitely be present at the forum.

---

### Post by coffeecat on 2008-08-22
I've never virtualised Windows in VirtualBox, but I've had good experience of virtualising Linux using a MacOS host with Vbox. If you want to try VirtualBox in Ubuntu, don't use the (older) version in the repositories. Download the latest 1.6 version from the [VirtualBox website]("http://www.virtualbox.org/"). There's a virtualisation subforum on this forum if you need help getting Windows going as a guest OS, and there's also a forum at VirtualBox.

I have no experience of VMWare, but I've seen good reports of it.

To expand on what **the_softy** said about reinstalling Windows. If you do, it will overwrite grub stage 1 on the mbr and you will only be able to boot into Windows until you've repaired grub. This is easy enough, but you don't have to create a new menu. The original grub menu and grub stage 2 will still be in the Ubuntu root partition. All you have to do is to reinstall grub stage 1 to the mbr. If you need to, simply post which partition your Ubuntu root partition is (sdb1, sda6, or whatever) and someone will be able to tell you how.

> **SaikoRonin said:**
> I do not use the windows version as, unbelievably theres a video and sound driver problem on it.

Unbelievably? :shock: No. Believe it. Believe it. :wink:

---

### Post by tangibleorange on 2008-08-22
VMware is excellent. there is a good guide on how to install it here:

[http://ubuntuforums.org/showthread.php?t=779934]("http://ubuntuforums.org/showthread.php?t=779934")

follow the instructions for v1.0.6. once you've installed it, you will need an XP install disk to install inside Ubuntu (in VMware).

---

