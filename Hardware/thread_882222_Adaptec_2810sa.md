---
title: "Adaptec 2810sa"
date: 2008-08-06
forum: Hardware
---

### Post by cbhatt on 2008-08-06
Hi all,
I have a raid array on an Adaptec 2810sa SATA raid controller on a computer whose OS shall not be named. I'm planning to remove the existing OS and replace it with Ubuntu. I don't care about the data on the disks and I will be rebuilding the arrays anyway. I will be running Ubuntu off the motherboard controller. The Adaptec card is for my NAS only.

What I'd like to know is the Adaptec 2810SA compatible with Ubuntu? Do I need to install any special drivers to make it work? If so, how do I do it?

Thanks in advance.
-Chirag

---

### Post by Cr0n_J0b on 2008-10-08
You probably already know this by now, but it is indeed compatible.  Your devices are built by the controller and shared to the OS as low level media devies.  I have this on my system and all I did weas init the array, build it, and save (from the card), then boot the system.  Linux sees the devices as a standard /dev/sda devices.  Format and mount...you are done.  I'm working on performance right now for my part.  It just seems really slow to me.  but the it's functioning correctly.

---

