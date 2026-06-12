---
title: "How do I duel boot vista with ubuntu 9.04"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Iwilllearn2 on 2009-05-04
I'm trying to install Ubuntu 9.04 as a duel boot with vista installed first. I printed off _How_ _to dual boot Vista with Ubuntu_ by Jonathan Schlaffer, but now I realize that was for an older Ubuntu because I'm not getting the same screens.

I would love a link to a step by step guide for installing Ubuntu 9.04 with vista installed first. I installed Ubuntu through wubi before but now I want more than 32GB of space for it.

I'm at the Prepare disk space step which is step 4 of 7, I have options:
Install them side by side, choosing between them each startup
Use the entire disk
Use the largest continuous free space
Specify partitions manually (advanced)

I have:
Windows Vista (loader) (/dev/sda1) 356.4 GB
Free Space 100 GB (I was told to make this in the outdated guide)
Windows Vista (loader) (/dev/sda3) 9.3 GB

---

### Post by Partyboi2 on 2009-05-04
Try this one
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Iwilllearn2 on 2009-05-04
I think I did everything right, but is this right? The warning looks intimidating!
Will I still have vista installed if I click Install

Language: English
 Keyboard layout: USA
 Name: daniel
 Login name: daniel
 Location: America/New_York
 Migration Assistant:
 Windows Vista (loader) (/dev/sda1):
 daniel: Mozilla Firefox, Internet Explorer, Wallpaper, My Documents, My
Music, My Pictures


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #6 of SCSI1 (0,0,0) (sda) as swap

---

### Post by Partyboi2 on 2009-05-04
Yes to both questions and yeah it does look intimidating the first time round.

---

### Post by Cuba71 on 2009-05-04
I must be missing sosmething, I installed Jaunty in my Laptop running Vista, and din't have to go through any of the complications indicated above.
While runnin vista I inserted the 9.04 CD and Ubuntu was installed without a problem.
The only thing I did after the installation, was to modify Vista's boot.ini to make Ubuntu the default.

---

### Post by Partyboi2 on 2009-05-04
> **Cuba71 said:**
> I must be missing sosmething, I installed Jaunty in my Laptop running Vista, and din't have to go through any of the complications indicated above.
While runnin vista I inserted the 9.04 CD and Ubuntu was installed without a problem.
The only thing I did after the installation, was to modify Vista's boot.ini to make Ubuntu the default.
Looks like you installed Ubuntu inside Vista using Wubi where as Iwilllearn2 is installing Ubuntu to its own partition.

---

### Post by wabbalee on 2009-05-04
first remove any files and uninstall any programs you do not need in windows, empty the bin and do a defrag (windows)
then use the gparted live cd (or if gparted exist on ubuntu live cd use that) to resize your windows partition to say 30gb, apply after each step. then (in gparted) create a new partition for Jaunty using ext4 fs (say 30gb?)
then create a linux swap partition (1gb should be enough) and use whatever is left for general storage to be accessible in both windows and ubuntu using the fat32 fs

then reboot into ubuntu cd and choose install ubuntu
step through untill you reach where it asks you about partitioning and choose 'manually'
in there you will see what you have just done with gparted. rightclick on windows partition and tell it to use it as ntfs (assuming it is what windows usues) but do not let it format. also let it mount it under say 'wxp' or whatever you want to call it. this way it will appear in your system under /wxp folder
use the 2nd partition for ubuntu and let it mount as / (that is a forward slash) it is ok to format this partition.
use the third for swap
and the fourth for storage (formatting not necessary) and tell it what the fs is (fat32) and let it mount it as /storage so like the wxp partition it will show in your system as /storage

easy peasy

---

### Post by Iwilllearn2 on 2009-05-04
Thank you for all the help, I now have a successful duel boot system!!!:guitar:

---

### Post by _graham_ on 2009-05-09
> **wabbalee said:**
> 
then use the gparted live cd (or if gparted exist on ubuntu live cd use that) to resize your windows partition to say 30gb


Just a warning to anyone resizing Vista partitions - I just tried to resize using gparted on a live cd. I used the "round to cylinders" option, which was ticked by default. I have since learnt that this screws up the Vista partition and I have not been able to get it to boot since.  I have read [here]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") (in the comments) that the "round to cylinders" option should not be checked.

I'm glad I followed the advice and made a backup of my system first!

---

