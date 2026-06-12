---
title: "External USB disk problem"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by Paul Cloesen on 2005-12-21
First time I installed UBUNTU, whenever I plugged in an USB external storage device it was automatically recognized and a schortcut would appear on the desktop.  Nice.  However, I need Windows as well to quickly do some specific things I don't know yet how to do with other software.

Partitioned my HDD.  Installed Windows in one partition and UBUNTU in another.  But no shortcuts to external USB storage devices anymore ! However, in System/Administration/Disks, the external HDD appears.  So I mounted it in a subfolder ("Iomega") of my home directory.  Nice, now I can see its contents. However, in the process, the subdirectory's owner is changed: it now belongs to root and access is limited to read only.  Since I am not allowed to login as root I cannot write to this disk.  Moreover, every time I reboot I have to mount it all over.

Tried to change owner of the subdirectory:
sudo chown paul Iomega
This asks for password and then says "Operation not permitted"

Tried to change its attributes:
sudo chmod -R a+rwx Iomega
This doesn't do anything: it doesn't even generate an errormessage.

Tried to share the directory:
Installed SAMBA
Nothing changes.

Tried to mount manually:
mount -t auto /dev/sda1 /mnt
"Only root can do this"  -  So we are at the same point again...

Contents of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
Seems that no provision is made here for USB drives....

I also see that on boot, everything goed fine (OK appears), EXCEPT for "starting Hotpulg subsystem.

What did I do wrong?  Why doesn't it mount automatically?  How do I get full access to this disk ?  I need it to make a backup and to have a means of communicating between the two operating systems on this computer other than emailing every file I need in Windows to myself !!!

Thanks in advance,

Paul

---

