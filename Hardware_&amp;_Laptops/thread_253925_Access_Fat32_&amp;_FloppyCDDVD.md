---
title: "Access Fat32 &amp; Floppy/CD/DVD"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by jadhav333 on 2006-09-09
I am currently planning to install ubuntu 6.06LTS on my PC after permanently removing the windows partion. I intend to use the ext3 filesystem for the same. 

Please resolve some of the queries stated below. 

1) If I format a drive on the same PC as FAT32, can I access/read/write on it in linux?

2) If I Write a floppy or Burn a cd/dvd in linux, will it be readable on standard windows pc? What filesystem would it need to be written in ,  on the floppy and the cd/dvd?

Thanks

---

### Post by HAARP on 2006-09-09
1) yes
2) yes. ISO9660 on the CD, FAT on the floppy

---

### Post by jadhav333 on 2006-09-09
1) But when i run ubuntu through the live cd, the computer tab shows the drives but doesnot allow access to the same. when i try to mount the drive it gives the following 

error:"/dev/hdc1 is not removable"
error:"couldnot execute pmount"

I am unable to access my ntfs as well as fat32 drives.

pls advise.

---

### Post by jadhav333 on 2006-09-09
I found this solution, some place on the net.. specifically to fix a bug in ubuntu 6.06

open a terminal. edit the file 'pmount.allow'

**$ sudo gedit /etc/pmount.allow**

append the following line in the file.

[B]/dev/hda1
/dev/hda2[/B]

and so on list all your devices.
save and quit the editor
right click and mount the drives in the computer tab of Nautilus.

Double click and enjoy the access to ur drives....
:)

---

