---
title: "RAID Advice"
date: 2008-10-04
forum: General Help
---

### Post by spherics on 2008-10-04
I'd appreciate some advice on configuring RAID.

I've set up Ubuntu Desktop 8.04LTS and created some network shares.  My network consists of a bunch of Windows XP and Linux machines.  I'd now like to set up a RAID 1 configuration to provide some protection of my stored data.  

The Ubuntu Desktop Machine uses an ASUS A8N32-SLI-Deluxe Motherboard which has two RAID controllers on board, a SATA interface and a GigaBit Ethernet.  The desktop has Ubuntu installed on the IDE0 disk and I plan to install two SATA drives two form a RAID 1 array, and mount my network shares there.  The RAID controllers are a NVIDIA nForce4 SLI and a Silicon Image 3132.

Q1.  Do the NVIDIA nForce4 SLI and a Silicon Image 3132 controllers on my Mobo support Hard or Soft RAID ?  

I assume the controllers support Hard RAID but I haven't really understood how to determine the difference.  The manual is not terribly helpful either.

The Mobo manual does provide guidance on the Bios utilities for configuring the RAID devices.

Q2.  Assuming it is Hard Raid what set up do I need to do in Ubuntu for the raid array ?

Q3.  Any tips advice on pitfalls I should avoid when setting up the network shares on the RAID array.

I'd really appreciate some advice.  I have searched the forum and read some of the previous posts on RAID, but I'm something of a Ubuntu novice and am having difficulty seeing the wood through all the trees so please be gentle with me.

---

### Post by _sAm_ on 2008-10-04
I think you should read this; [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by spherics on 2008-10-13
I've spent some time reading the guide and searching through other stuff in the forum and I'm still terribly confused.

It seems the controller I have is a "fake raid" controller.  Other threads suggest setting up fake raid is more trouble than using software raid and doesn't gain very much.  So I should go for software raid.

I'm confused whether I should be using DMRAID or MDADM to set this up ?

I have three disks, 1 IDE with a working Ubuntu system on it, and 2 SATA drives I want to use as a RAID 1 array for data storage only.  I don't want to put a boot partition on the SATA drives.

Any advice please.

---

