---
title: "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by Mnemonica on 2007-08-21
Alright, so I start the live CD from the BIOS and it runs great. A couple of errors about a logical drive something... It moves too fast for me to figure out what its saying. But the Live CD works. Ubuntu Live boots and I go to System -> Preferences -> Removable Drives and Media: Uncheck "Mount removable drives when hot-plugged" & "Mount removable media when inserted". Close.

Then...

System -> Administration -> GNOME Partition Editor: It looks like this...

Partition                            | File system                | Size

/dev/sda1 |*!-in-triangle*| Unknown file system | 40 Gig
/dev/sda3 |*!-in-triangle*| ntfs                            | 67.20 Gig
*Down Arrow*/dev/sda2 *padlock* | Extended  | 4.58 Gig
             / dev/sda5 *padlock* | Linux-swap         | 4.58 Gig


Ok, so now I right click /dev/sda1 and select format to -> est3
I hit apply. It either completes the operation, or I receive the error "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

I hit close or ok and then all partitions disappear completely. No hard drive can be found in either the installer or gparted. I've tried going directly through the install and I always get the previously mentioned error through that route. When I reboot, I can see the partitions, but the previously formated to ext3 part is unknown again.

What the hell is going on?

I posted earlier and got some help on trying to repair a HDD that had a magnet scraped across it. And now I can see the harddrive in BIOS and Ubuntu's Live CD but can't load linux to it. Or, rather, can't get the correct partition to format.

PS. I'm running a Dell Inspiron 640m

---

