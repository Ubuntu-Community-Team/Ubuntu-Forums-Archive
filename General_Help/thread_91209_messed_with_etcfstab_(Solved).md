---
title: "messed with /etc/fstab (Solved)"
date: 2005-11-16
forum: General Help
---

### Post by stknightmare on 2005-11-16
I messed with /etc/fstab trying to pass writing permission  
/dev/hda5 / umask=0000 0 1
it should be /dev/hda5 / defaults,remount-ro 0 1 

Any ideas?

---

### Post by invalid on 2005-11-16
What exactly is it that you are asking..

---

### Post by kruz on 2005-11-16
wait u messed it up
and you know what it should be
whats the problem?

---

### Post by stknightmare on 2005-11-16
Sry i changed the /etc/fstab and now ubuntu does not boot up.I can go only to recovery mode.The problem is that i changed defaults,remount-ro with umask=0000.If i can open /etc/fstab and edit it i will bring it back to its normal state.

---

### Post by kruz on 2005-11-16
boot with the cd
enter recovery mode(not sure hit f1-f7? to find that option)
should boot u to a non x window system
type

sudo nano /etc/fstab

or w/e u wana edit

nano or vi wutever ur more comfortable with

---

### Post by stknightmare on 2005-11-16
Ok stupid gedit,i boot up in recovery mode and used nano to edit /etc/fstab

But when i try to save the file it says read-only file system.

---

### Post by Maverick911 on 2005-11-16
You need to either use sudo or log in as root to edit the file.

---

### Post by Robgould on 2005-11-16
before you try to edit the file, run
 
sudo chmod 777 /etc/fstab
 
this will give everyone full rights to the file
 
I leave mine like this, but if you are worried about security change the permissions after.
 
Another way is to just run
 
sudo gedit /etc/fstab
 
that will give you su rights to the file.
 
Hope this helps

---

### Post by stknightmare on 2005-11-16
ok fixed.10x every one.

---

