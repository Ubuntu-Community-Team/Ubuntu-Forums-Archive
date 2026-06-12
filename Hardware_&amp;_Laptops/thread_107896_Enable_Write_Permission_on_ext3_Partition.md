---
title: "Enable Write Permission on ext3 Partition???"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by maxbaggi on 2005-12-24
Hi everybody, I just finished installing Kubuntu 5.10.  I manually created three ext3 partitions and one FAT32 partition during the partitioning stage.
After finishing the installation I managed to turn on write permission on the FAT32 partition by replacing the original line (can't remember what it was) in etc/fstab with the following line:

/dev/hda9 /media/hda9 vfat umask=000 0 0

How do I turn on write permission on the ext3 partitions?

My fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda7       /media/hda7     ext3    defaults        0       2
/dev/hda8       /media/hda8     ext3    defaults        0       2
/dev/hda9 /media/hda9 vfat umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0```

```

---

### Post by anil_robo on 2005-12-25
I had a similar problem when I created another ext3 partition after running ubuntu for several days, because I wanted to install windows XP on it using vmware. Im not an expert, but I did the following:
```
sudo gedit /etc/fstab
```
Then I found out the partition I just created (hda6, hda7 and hda8 in your case), and changed some options in the fstab file. Which options:
Under the options field in fstab, you'll notice "default" written for hda6,7, and 8. Change that to rw.... then...
Reboot.

You should have write access to your partitions. If still you don't have it, you can try one more thing. open a terminal window and type
```
sudo nautilus
```
This opens nautilus in root mode. I do it frequently to avoid terminals.
Then go to your /media/ folder and see hda6,7,8 listed there.
For each, right click and enable read, write and execute permissions for everyone.... then...
Reboot.

You should have write access to all those partitions!

If you don't see those partitions mounted, you can force manual mount by ```
sudo mount -a
```
I got all this info from [www.ubuntuguide.org](www.ubuntuguide.org) !
:)

Let me know if it worked out! :)

---

### Post by maxbaggi on 2005-12-25
Thanks anil_robo, it worked!

---

