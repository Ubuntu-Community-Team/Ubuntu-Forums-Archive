---
title: "mdadm raid 0 on 2 devices cant get back info"
date: 2008-11-08
forum: General Help
---

### Post by jalfan on 2008-11-08
Hello World!

I had xubuntu with gnome-desktop environment running and I had used mdadm to combine both my 250 GB (sdd) and 160 GB (sdb) hard drives to make one drive and had it (dev/md0) mounted in my /home directory.  I had my OS on a separate drive (sda).  I have a fourth drive (20GB sdc) that I tried to install Debian Etch onto.  The install was sucessful, but I had to change some things in my BIOS to get it installed.

After the changes to my BIOS (had to change from Enhanced mode to Compatibility mode for my IDE devices - ASUS P5PE-VM Motherboard) I could only see hard drives on either th eprimay or seconday IDE port.  So in order to fix this I had plugged in an IDE PCI card (which I learned had a hardware-RAID on it.  I had gone into the hardware raid configuration to check it out, but when I plugged my system back the way it previously was, I could not boot back to my Xubuntu drive and had to re-install, 

Once I was done I installed mdadm and tried to re-create my raid0, but now my 250 GB drive is showing as unallocated.  the 160 GB drive still shows as a linux raid drive, but I can't seem to get them raided together (after creating /dev/md0 I cannot mount it because it is showing the 250GB as unallocated and not as ext3 or raid as it used to be).

Is there any way that I can tell my OS that it is a linux raid or ext3 without deleting all the info on the drive?

If I run fdisk, it doesn't show a partition for the drive.... is there nothing I can do to get my data back?

--Thanks for any and all help

--Jalfan

---

