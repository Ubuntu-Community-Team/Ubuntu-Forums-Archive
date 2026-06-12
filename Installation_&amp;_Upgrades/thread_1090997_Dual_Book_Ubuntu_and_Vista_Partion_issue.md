---
title: "Dual Book Ubuntu and Vista Partion issue"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by rman71 on 2009-03-08
I want to dualboot Ubutnu and Visa 32 on my Acer 6930 notebook.  Vista is already installed with 4 partions (factory defaults), C,D, Restore, etc..  If I go into Vista and shirnk an existing partion, the space that is now available is not usable.  

Not sure what I need to do. Please help if you can.

Thanks

R

---

### Post by HeretikSaint on 2009-03-08
Yeah I am having the same issues.  Apparently Vista puts its system files all over the disk so when you go to "shrink" the partition, it can't because vista system files are scattered all over the drive.  I am currently trying this method:
```
http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/
```
I'll post back here if it actually worked or not.

---

### Post by Mark Phelps on 2009-03-09
Without seeing the partition map, I'm guessing, but it appears you already have four partitions.  If they are all Primary (my guess), creating a new empty space won't allow you to create another partition because the limit of primary partitions on a drive is 4.

If the last partition on the drive is only a data partition (not an OS or recovery), you need to replace it with an extended partition.  You would need to back off the contents of that last partition to external media, remove that partition, create a new extended partition, and recreate the previous partition inside that -- leaving room for Ubuntu.

While you could probably do this from a LiveCD, I would recommend going to Distrowatch website, downloading Parted Magic, burning that ISO to disk, and booting with that.

---

### Post by Corbin Dallas on 2009-03-09
I've found this article to be very helpful for dual boot. Not so much triple boot, but dual for sure.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by 41214 on 2009-03-10
My shrink utility won't work, it says access is denied and so far I haven't been able to find a fix for it. Any ideas?

---

