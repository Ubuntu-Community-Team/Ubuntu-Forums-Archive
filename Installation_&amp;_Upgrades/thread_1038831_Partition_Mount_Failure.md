---
title: "Partition Mount Failure"
date: 2009-01-13
forum: Installation &amp; Upgrades
---

### Post by Jonathan^ on 2009-01-13
I am trying to install Ubuntu on my desktop machine and have run into a problem with the partitioning. The installation runs fine until the "Partitions formatting" section of the install (about 5% in), when I recieve the following message:

"The attempt to mount a file system with type ext3 in SCSI7 (0,0,0), in partition #1 (sda) at / failed.

You may resume partitioning from the partitioning menu."

Returning to the partitioning menu (I used the "Guided - entire disk option" the first time), I next chose the "Guided - resize SCSI7 and use free space" option. Same message. Returning a second time, I decided to use the manual partition option. My partitions:

/dev/sda5 4 GB swap
/dev/sda2 20 GB ext3 (mount point "/")
with 96 GB free space (for Windows, if I decide to reinstall it later)

Same message during the installation, with a 2 where the "1" was before.

I used to have Windows XP installed on the hard drive I am attempting to use, but I accidently erased it off why trying to get the partitions to work. No harm done though, as I didn't have any critical files on it. I'm not sure if this could cause any problems with the install, so I am just throwing it out.

Any suggestions?

---

### Post by Partyboi2 on 2009-01-14
Try using gparted from the Ubuntu live cd (System>Admin>Partition Editor)  to create the partitions before running the installer. Then run the installer and choose manual and set the mount points.

---

