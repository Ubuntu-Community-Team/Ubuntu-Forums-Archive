---
title: "Gparted CAN REZISE?:("
date: 2008-08-13
forum: General Help
---

### Post by juniorn on 2008-08-13
okey i have donloaded three programs for partiotion editing and in gparted i get this wrong message
couldnt open /dev/fd0 for both writing and reading (file system in radpoint). /dev/fd0 opened in readpoint.
in/out wrong under reaading on /dev/fd0

i cant rezise my hardrive how i do to fix it!

---

### Post by cmay on 2008-08-13
hi.
i think /dev/fd0 is the floppy drive.
/dev/hda or /dev/hdb is the harddisk.
/dev/sda shoukld be flashdrive/usbstick.

there is an option to select which drive to format in gparted
under menues.
hope it could help

---

### Post by juniorn on 2008-08-17
I dont think taht becouse my hardrive is 160gb and it have 160gb:( so didnt work anything else?

---

### Post by juniorn on 2008-08-17
its also the boot drive:(

---

### Post by Sinkingships7 on 2008-08-17
You have to do this on the live cd. You can't edit the partition your installation is on if you're using it. Alternatively, you could use the [gparted live cd]("http://gparted.sourceforge.net/livecd.php"), which would be easier and faster to burn if you have misplaced your live Ubuntu cd.

---

