---
title: "New HDD install gone wrong..."
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Surcouf on 2009-09-28
I was in need of more HDD space so I went and got myself a brand new Seagate ST31000528AS - 1 TB Sata drive - price was good!

While my system was out I installed the new HDD and booted up.
I did check the BIOS to see if the HDD was recognized.  No problem there.

After installing GParted from terminal, I was able to see my new HDD with a total of 953867 MB identified (dev/sdc).  I proceeded into formatting the HDD in one partition in ext3 format.  I want to use this HDD for archiving data.  Formatting went smoothly with final result of 931.51 GB ( 14.81 used + 916.70 GB unused).

Next, I installed PySDM Storage Device Manager from terminal as I needed to mount the HDD. I mounted the dev/sdc1 successfully.

Now here is the beef!  When I go back and try to access the drive I seem to have no permissions whatsoever. I cannot create folders, delete/copy files, etc.  In the file systems, where I can see /media/sdc1, I'm unable to have access either.  Where did I go wrong ](*,)
And I thought adding a new HDD was supposed to be easy under Ubuntu!

Thanks for your help!

---

### Post by earthpigg on 2009-09-28
did it work fine ***before*** you installed PySDM Storage Device Manager?

---

### Post by Surcouf on 2009-09-28
> **earthpigg said:**
> did it work fine ***before*** you installed PySDM Storage Device Manager?

I would not know as I did not try it then or before that install.
My reading of various sites on how to proceed with this new HDD installation lead me to the GUI of PySDM Storage Device Manager for mounting a HDD.  Some sites mentioned that it could also be done via terminal but I could not get the right info on it so I figured the GUI option would be a good one.
Is there a problem with this software?

---

### Post by presence1960 on 2009-09-29
> **Surcouf said:**
> I would not know as I did not try it then or before that install.
My reading of various sites on how to proceed with this new HDD installation lead me to the GUI of PySDM Storage Device Manager for mounting a HDD.  Some sites mentioned that it could also be done via terminal but I could not get the right info on it so I figured the GUI option would be a good one.
Is there a problem with this software?

You need to set permissions on the disk. here is a graphical way to do it. Open a file browser and mount the disk. You will be asked for password. Once the disk is mounted leave that file browser open. Now open a terminal and run ```
gksu nautilus
```
Again you will need your password. Click on file system, then open media directory. You will find a directory which is your mounted new hard disk. Right click that directory and choose properties. Click the permissions tab. Change the Users and Groups setting from "root" to your user name. Click Apply to enclosed files. Close all windows and you will now have read/write permissions on the disk.

---

### Post by Surcouf on 2009-09-30
> **presence1960 said:**
> You need to set permissions on the disk. here is a graphical way to do it. Open a file browser and mount the disk. You will be asked for password. Once the disk is mounted leave that file browser open. Now open a terminal and run ```
gksu nautilus
```
Again you will need your password. Click on file system, then open media directory. You will find a directory which is your mounted new hard disk. Right click that directory and choose properties. Click the permissions tab. Change the Users and Groups setting from "root" to your user name. Click Apply to enclosed files. Close all windows and you will now have read/write permissions on the disk.

You made my day!!!
Indeed, the problem was exactly what you pointed out and after following your directions I was able to gain complete access to my new HDD.
Thanks for your help **presence1960**!  Much appreciated!
Surcouf.

---

### Post by presence1960 on 2009-09-30
> **Surcouf said:**
> You made my day!!!
Indeed, the problem was exactly what you pointed out and after following your directions I was able to gain complete access to my new HDD.
Thanks for your help **presence1960**!  Much appreciated!
Surcouf.

Glad you got it working! Enjoy Ubuntu.

---

