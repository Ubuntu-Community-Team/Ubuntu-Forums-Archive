---
title: "Can't mount flashdrive on Hardy"
date: 2008-08-09
forum: General Help
---

### Post by mamboze on 2008-08-09
I've got a Kingston 2Gb DataTraveler flashdrive which I'm unable to mount on a Hardy machine. 
The drive is recognized by BIOS - plug it when in  BIOS it shows up on the BIOS window.

I had a look at 
[http://ubuntuforums.org/showthread.php?t=150412](http://ubuntuforums.org/showthread.php?t=150412)

Using the two terminal commands stated there:

carlos@medea:~$ sudo mkdir /media/usbdisk
[sudo] password for carlos: 
carlos@medea:~$ sudo mount /dev/sdd1 /media/usbdisk
mount: special device /dev/sdd1 does not exist

What needs to replace /dev/sdd1?

Any help appreciated.

---

