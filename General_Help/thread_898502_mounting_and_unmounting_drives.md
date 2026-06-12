---
title: "mounting and unmounting drives"
date: 2008-08-23
forum: General Help
---

### Post by Garratt on 2008-08-23
ok i know it's wrong to double post but i have been abandoned and no1 else seems to be helping...

[this is the thread]("http://ubuntuforums.org/showthread.php?p=5648921#post5648921")

basically i reinstalled ubuntu and my grub boot loader is backwards, i have 2 hdd's one 600g vista, 1 80g ubuntu, so i loaded up live cd,

i am trying to edit menu.lst i mounted:

sudo mkdir /media/slash

sudo mount /dev/sdb1 /media/slash

gksudo gedit /media/slash/boot/grub/menu.lst

unfortuantely

sudo mount /dev/sdb1 mounted the vista 600g hdd and i needed to mount the 80g hdd, i tried unmount: and got an error command not found.... can someone please pick this up and help me unmount and remount the correct hdd ?

---

### Post by aloshbennett on 2008-08-23
umount is the command :)

---

### Post by Garratt on 2008-08-23
so i'm screwed....

i just tried to mount on another folder and now it not doing anything like the 80g hdd doesnt exsist so im starting over :(

---

