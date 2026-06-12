---
title: "Where's My Mounted but Not Visible NTFS Partition?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-05
I think the general for NTFS partitions is that if the corresponding /etc/fstab entry uses /mnt/name as the mountpoint, the drive is designated with the leading hd__ for Hard Drive designation and stays mounted while showing up under Places on the top toolbar, but if it instead has /media/name as its mountpoint, it is designated with the leading sd__, which is taken as a SCSI drive, removable, and still shown under Places and on the desktop when mounted.  One or the other, with earlier releases of Ubuntu leaning towards the sd__ approach, and later versions towards the hd__ method instead.  A manual edit of /etc/fstab means either option can be applied.

What's interesting is what happens if the partition has a name or not,  If no label (no name), then the entry for that partition in /dev/fstab can have a folder of most any name set up for it in /mnt or /media, but you have to manually do a sudo mkdir /mnt/name or sudo mkdir /media/name to create the folder that needs to be there, and this name must match the name shown as part of the mountpoint for that entry in /etc/fstab.

But what if the partition has a label?  You can use that label for the name in the mountpoint part of the /etc/fstab entry, and if the folder is not in the designated /mnt or /media folder, it can be added, likely done automatically if not manually.

What can be weird though is for a labelled partition to be assigned a different name at the mountpoint area that does not match the label. This can still work, but again it requires a mkdir to add a folder of that name to either /mnt or /media to let it be mounted. But in this case, the surprising thing is that even though mounted, the partition will not show up under Places or as part of the file system.  It is as if once mounted, it just disappeared.  However, it is still there, and you can get to it by relating to the mountpoint, using that path and name when dealing with it.

To test any changes to /etc/fstab, /mnt, or /media, you can execute a sudo mount -a command in a terminal, where the -a means to try and mount all the drives.  To see what drives are now mounted, you would just enter mount by itself   That will list the status of each drive separately.

---

