---
title: "[SOLVED] unable to mount volume"
date: 2008-10-17
forum: General Help
---

### Post by qwertymodo on 2008-10-17
I'm fairly new to Linux, and I'm currently dual-booting with Vista.  I repartitioned my hard drive like so:

80gig NTFS - Vista system partition (I run a lot of large programs)
30gig ext3 - Linux root partition
110gig NTFS - main data partition
1gig swap space

I did it this way in the hope of moving my /home directory to the 110 gig partition.  I clicked on places in the GUI, then right-clicked on the volume in question and went to properties.  Somewhere in there was a place to choose the mount point, so I typed /home and rebooted.  Upon rebooting I am told I cannot mount the volume and receive the error

mount_point cannont contain the following characters: newline, G_DIR_SEPARATOR (usually /)

Basically I get the point that I went about it wrong, but now I can't even get the same properties menu when I right click, so I can't undo it.  How can I remove that mount point from the terminal?  I found another thread telling me how to do it right once it's fixed, I just need to fix it first.

---

### Post by Pro-reason on 2008-10-17
I don't use GNOME, but I think that it doesn't want you to put in the full path to the mount-point.  It just wants one word, like “Films”, so that it can mount the thing at /media/Films.

I seem to remember another thread on here, where someone had the same problem.

I don't know what GNOME settings to change, but please post the output of “cat /etc/fstab”.  It will probably work if we fix that file manually.

---

### Post by qwertymodo on 2008-10-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=978f906f-d4c4-4a43-a782-f5a59886bae0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7531c2ea-ebe7-49ac-8c10-dc67a0ebbb25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



from what I remember, the partition in question would have mounted as sda3...

---

### Post by Pro-reason on 2008-10-17
[This bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668") should be informative.

> 
Quamquam omniam nescio, nec nihil scio

&#8220;Although I'm ignorant of all of it/her, and I don't know nothing.&#8221; ??

---

### Post by qwertymodo on 2008-10-18
Found a simple answer in a link towards the end of the comments:

[http://ubuntuforums.org/showpost.php?p=5530231&postcount=44]("http://ubuntuforums.org/showpost.php?p=5530231&postcount=44")

Problem solved ;)

---

