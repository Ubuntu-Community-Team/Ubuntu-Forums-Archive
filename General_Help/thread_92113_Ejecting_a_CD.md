---
title: "Ejecting a CD?"
date: 2005-11-18
forum: General Help
---

### Post by E1000 on 2005-11-18
I had to reinstall HAL (hardware abstraction layer?) and anyways, ever since then i cant mount or eject my CD's normally, to mount an inserted CD I have to go to 
"System ->Administration ->Disks" and select "enable" under the CD drive options.

when it comes to ejecting a CD, if I press the button on the drive it does nothing, If i rightclick the icon on my desktop and select eject it says 
```
Unable to eject media
show more details
umount: only root can unmount /dev/hdc from /media/cdrom0
eject: unmount of `/media/cdrom0' failed
```
 
the only way do eject is by restarting or going back to the "Disks" menu again and disabling.... It seems the root of my problem is related to permisions, but i still dont know what to do. does anybody have any idea what I should do to fix this?

---

### Post by taurus on 2005-11-18
One solution is to look in your /etc/fstab to see what kind of settings do you have for your CD-ROM there...

---

### Post by invalid on 2005-11-18
Are you mounting them as root user? If so, they can only be unmounted by root as well.

Post a copy of /etc/fstab here.. maybe there is a problem that is preventing auto user mounting.
```
cat /etc/fstab
```

Cheers,
Cb

---

### Post by E1000 on 2005-11-18
```
# <file system> <mount point>   <type>        <options>       <dump>  <pass>
/dev/hdc        /media/cdrom0   udf,iso9660    user,noauto     0       0
```

related factoid:
I also noticed that during bootup, the last thing to hapen is
"starting HAL" (or something similar to that)
is this suposed to hapen at this time, or is it suposed to hapen after I start Xwindows, maybe since i reinstalled it, the boot procedure has been changed in such a way to effect permisions? or then again maybe its suposed to hapen exactly at this time, i cant remember how it was before i reinstalled it.
any thoughts?

---

### Post by schdefan on 2005-11-18
The problem can cause the gnome-volume-manager
if you do a > ps -A | grep gonme-volume-manager 
do you see that it is running?

---

### Post by E1000 on 2005-11-18
i did 
ps -A | grep gonme-volume-manager
and 
ps -A | grep gnome-volume-manager

but nothing showed up, i dont think its running, i also added myself the the "disks" group and nothing hapened, does anybody else have any ideas?

---

### Post by E1000 on 2005-11-18
it seems my problem is that it doesnt auto mount the drive, because even as a user I can manually mount and unmount the drive, i think the reason it gives me the permissions error is because i used the disks menu (which requires password to use)

so all I really need to do is figure out how to change the settings on my system to get the CD to be automatically mounted... anybody know how to do this?

---

### Post by invalid on 2005-11-19
Way back toward the begining of your post, I advised you to post your fstab.
```
cat /etc/fstab
```

You may have a problem here, that we can fix if we see what is going on.

Cb

---

