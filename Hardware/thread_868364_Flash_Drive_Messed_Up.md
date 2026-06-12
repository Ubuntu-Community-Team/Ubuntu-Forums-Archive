---
title: "Flash Drive Messed Up"
date: 2008-07-23
forum: Hardware
---

### Post by Luft on 2008-07-23
I'm running Ubuntu 8.04 with the Kubuntu desktop.  I have a 4Gb Flash drive (my flash) that no longer allows me to add/remove stuff.

I can't use fdisk to delete and recreate the partition because the drive is mounted.  When I sudo **umount /dev/sdb1** the drive unmounts and then quickly remounts!

---

### Post by Dark_Stang on 2008-07-23
Does it say it's full? Why won't it let you add/remove files?

Edit: If it says it's full, but you don't think it is, check to make sure the trash is emptied.

---

### Post by Luft on 2008-07-25
The flash drive is getting worse.  It no longer shows any files.  It won't allow me to save anything it.  

gparted and qtparted can't fix it.  I'm pretty much stuck.

---

### Post by Dark_Stang on 2008-07-26
It's probably gone bad then. Just pickup a new one. You can usually get a 4gig one for less than $30 at best buy or off newegg.

---

### Post by Herman on 2008-07-26
How old is it and how much have you used it?
I have read that flash memory has a limited lifespan and I'm interested in learning more on that subject. :)

---

### Post by Luft on 2008-08-01
I've had it for less than a year and haven't used it much.  It may have failed.

---

### Post by finito on 2008-08-01
Do some icons have a lock on them?

if so then try using terminal copy somthing.

sudo cp <filepath/filename.ext> </media/<name_of_Drive>

see if it works, if so,then:

this will tell you if it works or not to correct this problem you have to change somthing in fstab.

---

