---
title: "can anyone tell if my usb stick is broken"
date: 2008-08-12
forum: General Help
---

### Post by cmay on 2008-08-12
hi.
i have question about a usb stick that i cant seem to get to work. its not responding to any treatment at all. i have tried to use gparted and dd and it wont let me format it so i can use it for storage or any usb pendrive linux distro.
now i just want to use it for back up since i dont have any rw cd or any other things to use as back up than floppy and my new computers dont have a floppy drive installed.

i have seen somewhere that usb sticks can be broken from the factory and i wonder if its simply the problem. i dont know how to find out what the course of this problem is.

i have five really old computers and a new computer and its the same problem on all of them.
i have ubuntu debian and desktopbsd  and i cant get anywhere near the pendrive at all.
so its not ubuntu related problem. 
 
 its a 1 gigabyte pleomaxflashdrive.
i have had data on it two years ago when using windows but thats lost i guess.
i have no windows no more so i cant see if its working on a windows machine.
i would be highly thankfull if anyone could help me whit this issue.

---

### Post by nazish on 2008-08-12
are you able to mount it?? or your problem is that you can see the drive but cant write data to it?

---

### Post by cmay on 2008-08-12
hi .
thanks for the reply. 
i posted the error message from my debian installation i am on now.

```
ibhal-storage.c 1344 : info: called libhal_free_dbus_error but dbuserror was not set.
libhal-storage.c 1345 : info: called libhal_free_dbus_error but dbuserror was not set.
libhal-storage.c 1401 : info: called libhal_free_dbus_error but dbuserror was not set.
process 4366: applications must not close shared connections - see dbus_connection_close() docs. this is a bug in the application.
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

error: could not execute pmount
```
whenever i try to mount it or even after i tried to install a usb distro dsl on it gparted tells me that all is fine i try move it to the computer i need to back up  some letters that are very important so i can fix the computer. its old and there is nothing on the drive suddenly. it cant be mounted and gparted dont see it  as a ext3 filesystem like i just thourght i had formatted it on the other computer. if i install something like pc linux it will look like the installation is on the stick until i reboot but then gparted tells me again there is nothing on the drive at all.
this is strange and i cant say that i am sure i am not the problem. maybe i do something all wrong.
thanks for the time.

---

### Post by nazish on 2008-08-13
you are most likely to get this error if you drive is not ejected properly. please make sure that when ever you need to remove the USB right click on the drive's icon and select eject. If this doesnt work try the lazy umount command.
> sudo umount -l /media/[YOUR DRIVE LOCATION]
 
also in case of failed mounts you can check if the following command is of any help.
 
> 
sudo fsck -v /dev/sdb


---

### Post by cmay on 2008-08-13
i plugged it and tried to mount umount and ran this fsck command. output is this.
> fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
The superblock could not be read or does not describe a correct ext2filesystem.  If the device is valid and it really contains an ext2filesystem (and not swap or ufs or something else), then the superblockis corrupt, and you might try running e2fsck with an alternate superblock:    e2fsck -b 8193 <device>

thanks for the time.

---

