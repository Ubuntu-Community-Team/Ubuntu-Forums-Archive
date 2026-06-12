---
title: "deleting files off usb drive"
date: 2011-10-12
forum: Hardware
---

### Post by hollowhead on 2011-10-12
I bought a iomega 1000gb USB hard drive.  I use it to back up by dragging and dropping my home folder to it.  This works fine.  The problem is its full.  If I try to delete files when I come to use the trash applet it comes up with a message in nautilus about preparing to delete.  Half an hour later it still says the same.  Is there a way to do this at less than geological speed?  Using the command prompt?

---

### Post by deltacomp on 2011-10-12
Have you tried changing directories to the USB Drive?  cd /media/drive-name then once your are in the drive, rm filename

---

### Post by kolinab on 2011-10-12
I back up to an external USB drive like you.

You might want to try a tool called grsync to handle your backups - it's simple and fast. Search for it in Synaptic or the software centre.

Regarding deleting files - if you're sure you want to empty the trash on your drive - what I do in this situation is push CTRL+H to show hidden files, then select your .trash folder and hit 'delete.' It shouldn't take too long. 

In the future, you can check under Edit . . . preferences . . . behaviour in nautilus, and add the option to include an option to delete files bypassing the trash entirely. This should prevent you having this problem again, but be careful . . . one keystroke and those files are gone.

I'm not sure using the command prompt will speed anything up for you. 

Post back with results and good luck,

K

---

### Post by hollowhead on 2011-10-12
Trying to delete the folder laptop 11th jan

nrh1@nrh1-linux:/media/Iomega HDD$ rm -ri /laptop /11th jan\

just showed > and didn't do anything

nrh1@nrh1-linux:/media/Iomega HDD$ rm -rf /laptop /11th jan\

does nothing at all

deleting the trash folder gives an error message that you shouldn't do it but it works -I assume its automatically recreated

Will look at grsync.

Thanks

---

### Post by deltacomp on 2011-10-12
> **hollowhead said:**
> Trying to delete the folder laptop 11th jan

nrh1@nrh1-linux:/media/Iomega HDD$ rm -ri /laptop /11th jan\

just showed > and didn't do anything

nrh1@nrh1-linux:/media/Iomega HDD$ rm -rf /laptop /11th jan\

does nothing at all

deleting the trash folder gives an error message that you shouldn't do it but it works -I assume its automatically recreated

Will look at grsync.

Thanks

Hi, Try this, rm -R 'laptop 11th jan'

---

