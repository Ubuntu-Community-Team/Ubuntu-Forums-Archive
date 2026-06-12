---
title: "Can't access hdb1 to change permissions"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by joeinazyes on 2006-08-28
I have 2 80GB hard disks listed as hda1 and hdb1.  I want to set the Permissions tab on hdb1 to the same access as my /home directory so that I can write, delete, and access my hdb1 drive with ease.  I previously had my drive formatted in ext3.  I just now reformatted it in fat32.  I followed the link below, before, and had success.


[http://ubuntuforums.org/showthread.php?t=234769](http://ubuntuforums.org/showthread.php?t=234769)


HOWEVER, now I cannot set the permissions tab by opening a nautilus window and get the following error message:


-desktop:~$ gksudo nautilus
(nautilus:5440): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
seahorse nautilus module initialized

** (nautilus:5440): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_owner


Again, the point is that I want to have unlimited share and access to hdb1 without constantly typing in /root permission.  Why won't this work now?

Here is my etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by coffeecat on 2006-08-29
Try changing your hdb1 fstab line to:

```
/dev/hdb1     /media/hdb1    vfat    defaults,utf8,umask=000  0 0
``` 
and reboot. I have a couple of variations that also work with vfat partitions on other machines, so post back if you have problems with that one.

**Edit:** I've just noticed your hda1 line. That is one of the variations I mentioned. Just copy the fourth field (defaults,utf8,umask=007,gid=46) to the hdb1 line and all should be well. Or try both. :)

---

### Post by joeinazyes on 2006-08-29
Thanks for posting Coffeecat.  I did exactly what you suggested in copying the string from the vfat swap partition and it works the way that I want it.

I appreciate your post!

---

### Post by psudo nym on 2007-09-03
Hi

I am am having similar problems. i am trying to network share 3 folders on a 120 gig drive labled as sda1. I dont want to share the whole drive just the 3 folders with music etc. 

i can see the folders on my widows machine when i try to add a network place it will not alllow me. 

i have tried using sudo nautilus and then tried changing the owner from root to paul. (me) I get *"Sorry, couldn't change the owner of "albums"*. error message.  and on looking back into terminal i get 
*** (nautilus:25026): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_owner.*

Any ideas please??:confused:

I will say at this point I'm already stretching my Linux abilities to the max so instructions like "edit your fstab file" and so on don't really make sense without "click here enter xxx, click..."

I am trying, but command line interface is just too like cavemen rubbing sticks together vs the big blowtorch in my shed. That said Ive only been using Ubuntu for a week and hope to learn more..

Any help would be very much appreciated!:)

Regards.

---

