---
title: "sata automount please!"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by drews_blunted on 2005-07-03
Ive had a 200 gig sata backup hd on my system for some time now, it is formatted to 1 200 gig ext3 partition. Currently to get the drive to mount i need to type:

sudo mount /dev/sda /media/sata

What im woundering is, what can i do to my fstab or whatever may be needed to make the sata hardrive automount each time ubuntu is started!

My fstab looks like this:

/dev/sda        /media/sata     auto    defaults        0       1 

My best guess, didnt work!

---

### Post by jeremy on 2005-07-03
The first and only partition on my 2nd SATA drive is mounted thus:

/dev/sdb1 /media/sdb1 ext3 user,auto 0  0

I had to create the /media/sdb1 folder and set the permissions. If yours is the 1st SATA drive you could try sda1 instead of sdb1

---

### Post by drews_blunted on 2005-07-03
yea, i tryed doing this to my fstab, except i dont have a /dev/sda1 so i used /dev/sda again. Still no luck it didnt auto mount.

---

### Post by drews_blunted on 2005-07-04
so does anyone know how to fix this, im sure its not a hard one

---

### Post by raghav_p on 2005-07-04
can't you just do something like:

/dev/hda2       /media/folder  ext3    nls=utf8,umask=0222 0       0?

I did this in an ext2 partition on my hd.. that worked.

---

### Post by djpenguin on 2005-07-04
You have to have a number to indicate the partition on the disk in order to mount it.

If you have placed one large ext3 partition on the disk, then it is sda1

Add that 1 to your fstab, and I'd wager it will work fine.

---

