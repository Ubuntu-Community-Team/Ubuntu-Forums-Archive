---
title: "new hard disk is just read only"
date: 2012-05-13
forum: Hardware
---

### Post by solbjorn on 2012-05-13
hi, 
i have a problem. i have just bought a new hard disk (extern) and my ubuntu is recognizing it but when i try to copy something in to it, it just says that this is not possible because it is just a read only. 
with a right mouse click i can get to the properties but i cant change the setting from read only to write and read :o 

can anybody help me?

---

### Post by Enigmapond on 2012-05-13
What file system is the external? ext3/4 Fat32 or NTFS?

---

### Post by solbjorn on 2012-05-13
it is a ntfs

---

### Post by Enigmapond on 2012-05-13
You can install ntfs-config which is a very simple utility to mount with the proper permissions or see this tutorial...
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
personally the ntfs-config is the easiest.

---

### Post by solbjorn on 2012-05-13
thank you
i tried it but it didn't work in this link i have to edit something but in my terminal it looks totally different than in that on the page :confused:

it says it should look like this: 

proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
**/dev/hda1       /media/hda1        ntfs    defaults        0       0**
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0 


but in my terminal it looks like this: 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fe32fa17-727d-4893-aba2-f3734baf8f9a /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=e6dd3491-8563-44de-bea0-84c72eecece3 none            swap    sw           $







                             [ 12 Zeilen gelesen ]
^G Hilfe     ^O Speichern ^R Datei öffn^Y Seite zurü^K Ausschneid^C Cursor
^X Beenden   ^J Ausrichten^W Wo ist    ^V Seite vor ^U Ausschn. r^T Rechtschr.

i really dont know why?

---

### Post by ahallubuntu on 2012-05-13
Devices won't be listed in fstab unless you have put them there - to mount a device automatically upon boot.  You probably DON'T want your external drive in there unless you will always have it plugged in and turned on when you boot your computer, otherwise you'll have trouble booting when that device is missing.

If you will always use this drive with Ubuntu and never with Windows, you can just format the drive (erase everything on it) as ext4 not NTFS.  You can do that in various ways, but the easiest may be a tool called Gparted.  You can delete the existing partition (after unmounting the read-only NTFS partition) and then make a new one and format as ext4.  But you won't be able to use any files on it in Windows without special drivers (that may or may not be that reliable).

---

### Post by solbjorn on 2012-05-13
hm 
i thought about geparted but i want to use it on windows too. so that would be a problem. 
of yourse i will try that, if there is no other way, but there must be a way to configure the hard disk that i can copy things on them on linux

---

### Post by wilee-nilee on 2012-05-13
> **solbjorn said:**
> hm 
i thought about geparted but i want to use it on windows too. so that would be a problem. 
of yourse i will try that, if there is no other way, but there must be a way to configure the hard disk that i can copy things on them on linux

I use gparted to make NTFS partitions for windows installs, never had a fail, reformat the external.

---

### Post by solbjorn on 2012-05-13
thank you so much for your fast help :) 

i solved it with the help of this page

[http://www.noobslab.com/2011/12/install-ntfs-configuration-tool-and.html](http://www.noobslab.com/2011/12/install-ntfs-configuration-tool-and.html)

now it works, i hope that it will stay this way. 

thanks again to everybody

---

### Post by Filthy Stockings on 2012-05-14
Thanks for posting this.....spent over 12 DAYS trying to get the same help but your posted link to outside these forums was the solution for me.

---

