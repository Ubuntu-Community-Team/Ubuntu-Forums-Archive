---
title: "Wanting to dual boot XP and Ubuntu.  How do I keep the recovery partition intact?"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by Sonicdude41 on 2009-04-11
Let me go ahead and list my PC's specs, if needed:

eMachines T5048
160 GB Hard Drive (154.4 GB allocated to XP, 5.6 GB allocated to recovery partition)
512 MB of RAM (Integrated Graphics Card takes 128 MB away, leaving me 384)
19" Flat Panel Monitor
CD/DVD Drive

That's about all I can think of.

Anyway, I am thinking about dual booting v8.04 of Ubuntu, but I don't want to hurt the recovery partition.  I am a newb to setting up a dual boot, just so you guys know. 

If I can't dual boot, would Wubi be the better choice?

---

### Post by Zw4nzig on 2009-04-11
Going to have to resize the XP Partition. Back up and have fun! Make sure to leave swap space!

---

### Post by Sonicdude41 on 2009-04-11
> **Zw4nzig said:**
> Going to have to resize the XP Partition. Back up and have fun! Make sure to leave swap space!

Okay.  Would I have to download GParted for this, or is there such a program in Ubuntu that allows me to make room for said partitions?  

Wouldn't making a new partition change the HD's partition table?  Just wondering.  

Also, where would I need to install GRUB?

---

### Post by ronparent on 2009-04-11
Consider creating an extended partition for installing ubuntu to. You already have two primary partitions and ubuntu would require two more. You are limited to four primary partition where as you can create as many logical partitions in the extended partition space as you want!

---

### Post by Mark Phelps on 2009-04-11
> **Sonicdude41 said:**
> Okay.  Would I have to download GParted for this, or is there such a program in Ubuntu that allows me to make room for said partitions?  

Ubuntu contains a version of GParted, but if you're installing 8.04, that's liable to be a year or more older than the current version.  Suggest you go to distrowatch.com, download and burn the most current GParted LiveCD and use that.

> 
Wouldn't making a new partition change the HD's partition table?  Just wondering.

Yes it will -- but partition management software knows how to do that.  So, as long as you don't mess with your recovery partition, you should be OK.  Just be patient using GParted because it can take a while to do its job.

> 
Also, where would I need to install GRUB?
The default will be to overwrite your MBR and install the GRUB files in your first Ubuntu partition -- which is OK if you don't  want to be able to go back to stricly XP someday or you have an XP boot disk so you can repair the MBR.

---

