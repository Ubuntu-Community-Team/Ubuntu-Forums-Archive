---
title: "Kubuntu 9.04 won't install to RAID correctly"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2009-05-18
Has anyone successfully installed Kubuntu or Ubuntu 9.04 to a RAID 1 with existing NTFS partitions, without wiping out the NTFS partitions?  I downloaded the Kubuntu 9.04 32 bit alternate desktop CD, but it wants to wipe the entire RAID 1 (made up of two, 1 TB SATA HDDs), instead of letting me put it on new or existing ext3 partitions.

FWIW, I am using one of those "fake" RAID chipsets, the Intel ICH9R, with two 1 TB HDDs in RAID 1 configuration.  I installed Windows XP SP3 to the RAID and would like to do the same with Kubuntu 9.04, for maximum data redundancy.  

Unfortunately, it appears the Kubuntu 9.04 installer can't see the existing partition structure.  The way things are actually configured is:

20 GB NTFS boot partition (Windows XP SP3 boot volume)
800 GB NTFS partition (used to store data)
*10 GB Ext-3 / partition for a previous Kubuntu 8.10 64-bit install
*4 GB swap partition that goes with the Kubuntu 8.10 install
*20 GB Ext-3 /home partition, again part of the Kubuntu 8.10 install
100 GB Ext-3 partition (can't remember the mount point, just used for general data storage)

The three marked with a * are logical drives on the same extended partition (if I have my terminology correct), for the maximum total of 4 primary & extended partitions, or 6 partitions overall.  I'm rounding up a little on the partition sizes, as a "1.0 TB" disk actually formats to something like 932 GB.

The only options I am offered all involve using the entire 1.0 TB "free" space (which isn't actually free!).  The installer insists on rewriting the RAID's partition table, promising to wipe out any existing partitions.

Is there some way to force the installer to see at least the NTFS partitions, so that it does not wipe them out when it installs Kubuntu 9.04?

---

### Post by dstew on 2009-05-19
There is a way. Basically, you install the program **dmraid** onto a Live CD system (yes, you can install to a Live CD system -- but any installed software goes away after you shut it down). This program gives the Live CD the capability to recognize and mount RAID filesystems.

However, installing is a pain. The automatic installer will not work with dmraid, so you have to install "by hand" by copying the file system to the RAID using the command line. See the [Fake Raid How-To]("https://help.ubuntu.com/community/FakeRaidHowto").

EDIT: Actually, it seems the ubiquity installer can now do most of the installation after dmraid is working and the RAID filesystem prepared. That is good news. Good luck.

---

