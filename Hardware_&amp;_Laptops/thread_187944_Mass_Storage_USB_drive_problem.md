---
title: "Mass Storage USB drive problem"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by michaeljb2005 on 2006-06-03
When the computer boots in it doesn't show an icon for my removeable USB drive.  If I go to System -> Administration -> Disks it will all of a sudden show it on the desktop but gives an error message that I don't have permission to view the drive.  Then if I disable and enable the drive it works and lets me have permission.  What can I do about this mount problem at boot?

---

### Post by chewbacca on 2006-06-03
I'm experiencing the exact same problem. From a terminal, however, I can access the drive as root (drive automatically mounted as /tmp/disks-conf-sdc1). It appears to be a permissions issue. I'll post a solution if I find one.

---

### Post by michaeljb2005 on 2006-06-03
Thanks

---

### Post by givré on 2006-06-03
You probably had a permission error because it is probably mount with fstab (let see your /etc/fstab) and your options are not set correctly.
If it works after you disable/enable your device, it's because at this time your device is mount by gnome-volume-manager. 

What i advice is to remove the line related to your usb drive in your /etc/fstab. It is safe if you don't have file needed by boot process in it (i.e. system files) and it will be mount automaticly by gnome when you will log in.

But let see first your /etc/fstab

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=givré]You probably had a permission error because it is probably mount with fstab (let see your /etc/fstab) and your options are not set correctly.
If it works after you disable/enable your device, it's because at this time your device is mount by gnome-volume-manager. 

What i advice is to remove the line related to your usb drive in your /etc/fstab. It is safe if you don't have file needed by boot process in it (i.e. system files) and it will be mount automaticly by gnome when you will log in.

But let see first your /etc/fstab[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by givré on 2006-06-03
Not really what i was thinking, i guess you have two hard-disks (sda and sdb), and if it that, there is nothing about your usb drive there, so it is not mount at boot time and you shouldn't have these permission error. I don't know what is wrong. 
Just to be sure, post your /etc/mtab when your usb drive is enable.

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=givré]Not really what i was thinking, i guess you have two hard-disks (sda and sdb), and if it that, there is nothing about your usb drive there, so it is not mount at boot time and you shouldn't have these permission error. I don't know what is wrong. 
Just to be sure, post your /etc/mtab when your usb drive is enable.[/QUOTE]

I just rebooted and for whatever reason it worked ok this time.

---

### Post by givré on 2006-06-03
[QUOTE=michaeljb2005]I just rebooted and for whatever reason it worked ok this time.[/QUOTE]
Cool ;)

---

### Post by michaeljb2005 on 2006-06-24
I am going to reopen this thread because after booting into kernel -25 the usb drive is mounting at bootup but not showing any files.  If I disable and enable the drive then it works fine.  But everytime I reboot I have to do this.  Any thoughts?

---

