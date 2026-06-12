---
title: "sticky for DM RAID issues at install"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Cr0n_J0b on 2009-11-01
I'm going through my 6th hour of upgrade hell, mostly associated with DMRAID issues.  Can I suggest that someone sticky or at least put a note one of the existing stickies in the installation forum about this?

My understanding is that DMRAID is broken or not functioning as expected in 9.10.  If you are like me and you have built volumes or are trying to build volumes using mdadm and software raid, you will be left scratching your head after you do a fresh install.  

Devices that you used to know and love will be renamed or lost and fdisk will not work as it used to...

IMO this is really bad stuff.  You will lose your data when DMRAID starts writing to your partition tables etc...

In my case, I'm fairly lucky.  i backed up most of my data before starting this project.

---

### Post by Cr0n_J0b on 2009-11-01
well, I haven't figured this one out yet.  I removed DMRAID, as someone suggested...and of course now my system won't boot.  I'm not sure what I was thinking...since DMRAID is the item that changed all of my device names in the first place...removing it just left no link to them...so there was no reference to my boot disk...duh..

I'm back trying to reinstall from the liveCD.  I'm trying to find a way to install 9.10 WITHOUT using DMRAID...wish me luck.

---

### Post by Cr0n_J0b on 2009-11-01
didn't work...I'm moving on to the alternative disk to see if there is more flexibility there.

---

