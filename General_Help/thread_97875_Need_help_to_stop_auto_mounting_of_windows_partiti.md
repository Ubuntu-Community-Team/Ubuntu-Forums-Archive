---
title: "Need help to stop auto mounting of windows partitions on bootup (Solved)"
date: 2005-12-01
forum: General Help
---

### Post by ndhskp on 2005-12-01
Hello

When I start my Ubuntu from a cold start it auto mounts all windows partitions and displays the little hard drive icons for them on the Gnome desktop.  I then have to System/Administration/Disk and select disable for each partitions.  Once I have done this they are now manual mount only until I reboot.  How do I stop auto mounting and make it so that they have to be mounted manually.  I did not have this problem with the downloaded iso of Ubuntu.  This only started when I got my official shipit CD-ROMs in the mail and installed from those.  Are the pressed (stamped?) CD-ROMs different from the downloaded iso?  I have windows on a separate hard disk.

Ubuntu 5.10

---

### Post by aysiu on 2005-12-01
What's the output of this command? ```
cat /etc/fstab
```

---

### Post by ndhskp on 2005-12-01
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/mapper/ubuntu-home /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       /media/hda7     vfat    defaults        0       0
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2005-12-01
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Then, delete the bolded text.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/mapper/ubuntu-home /home           ext3    defaults        0       2
[b]/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       /media/hda7     vfat    defaults        0       0[/b]
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` Save (Control-X), confirm (y), and exit (Enter).

---

### Post by soulestream on 2005-12-01
wouldnt it be better instead of deleting the entries, 
just changing defaults to noauto, user

that way you could still mount with just sudo mount /mnt/windows


soule

---

### Post by RAOF on 2005-12-01
[QUOTE=soulestream]wouldnt it be better instead of deleting the entries, 
just changing defaults to noauto, user

that way you could still mount with just sudo mount /mnt/windows


soule[/QUOTE]
Or, since you've added the "user" flag, just "mount /media/hda1" etc.  No need for root privs ;)

---

### Post by ndhskp on 2005-12-01
In my case I prefer not to really have access to my windows disk.  Windows is pretty much used for gaming.  Allthough for other people that will be different of course.

---

### Post by aysiu on 2005-12-01
[QUOTE=ndhskp]In my case I prefer not to really have access to my windows disk.  Windows is pretty much used for gaming.  Allthough for other people that will be different of course.[/QUOTE] Solved, then?

---

### Post by ndhskp on 2005-12-01
Thank you Aysiu.  I just rebooted to see if it would really work and now every thing is just peachey.  It's too bad really that the Ubuntu 5.10 starter guide does not show you how to stop auto mounting as it shows how to set up auto mounting.  Maybe some one could post a howto on stopping auto mounting of windows partitions.  I guess it would depend some on your fstab but still.  Or some one could post a link to a guide about the fstab file that explains the various options.

---

### Post by aysiu on 2005-12-01
[QUOTE=ndhskp]Thank you Aysiu.  I just rebooted to see if it would really work and now every thing is just peachey.  It's too bad really that the Ubuntu 5.10 starter guide does not show you how to stop auto mounting as it shows how to set up auto mounting.[/quote] To tell you the truth, in the past seven months, I have never seen anyone who's wanted to stop the automounting--you're the first one. 

> Maybe some one could post a howto on stopping auto mounting of windows partitions.  I guess it would depend some on your fstab but still.  Or some one could post a link to a guide about the fstab file that explains the various options. Go for it! We're behind you 100%.

---

