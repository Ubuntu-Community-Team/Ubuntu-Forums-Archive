---
title: "grub boot problem after gparted"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by jmurch on 2009-06-07
Nothing will drive you away from windows as fast as having vista......

I have been running dual-boot ubuntu 9 and Vista.  Since I rarely use
windows any more I wanted to reduce the size of the windows partition
and increase the size of the ubuntu partition.  I also have a 'recovery
partition' on my thinkpad.

After successfully running gparted from the live CD ubuntu boots same as
before.  At the end of the grub list I have /dev/sda1 (the recovery
partition) and /dev/sda2 (vista).  No matter which I select from grub it boots the recovery partition.  

Is this possibly because gparted hosed the vista install and the bad vista boot is falling back to the recovery boot?  

The vista partition is still flagged boot so I would presume that's where grub is so anything I can modify is in menu.lst?

If vista is hosed i will just gparted to whold hd to ubuntu but i would like to get this fixed so i can access old files in vista.

TIA, Jeff

---

### Post by Mark Phelps on 2009-06-07
> **jmurch said:**
> Is this possibly because gparted hosed the vista install and the bad vista boot is falling back to the recovery boot? 
Yep, sure is.  I've posted dozens of time in this very forum warning people about just the problem you've experienced -- using GPArted to resize the Vista OS partition.  

> 
If vista is hosed i will just gparted to whold hd to ubuntu but i would like to get this fixed so i can access old files in vista.


Just boot from the live CD, install ntfs-3g and ntfsprogs via synaptic.  Double-click the Vista partition in Places.  You should then be able to drag and drop your files from Vista to where you want to save them.

---

### Post by jmurch on 2009-06-07
Thanks that worked. I am able to get to any files in vista from ubuntu.  Is there any way to make vista bootable from grub since I can access the windows files?

Jeff

---

