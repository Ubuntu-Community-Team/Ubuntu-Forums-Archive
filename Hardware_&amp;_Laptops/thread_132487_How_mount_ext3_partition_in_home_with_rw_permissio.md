---
title: "How mount ext3 partition in home with rw permission?"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by feryllt on 2006-02-18
Hello,
   I have a problem. I have to mount an ext3 partition on a folder in my home with read/write permission. I don't know how I can do this...

Thanks!

---

### Post by knalle on 2006-02-18
mount -t ext3 /dev/sdx /place/to/mount

also try **man mount**

---

### Post by feryllt on 2006-02-18
Thanks but my problem is quite different.
I have to mount ext3 hda1 on */home/pippo/tmpmnt* and **pippo** user needs to be able to write on */home/pippo/tmpmnt* (like every other folder in his home).

Thanks ...

---

### Post by knalle on 2006-02-18
[QUOTE=knalle]
also try **man mount**[/QUOTE]

**mount** has options for how read, write and user/groups are handeled, read the **man**.

---

### Post by Sutekh on 2006-02-19
What mount command have you tried?


I wasn't able to do this by using the **mount** command.

Here's what I had to do to achieve this with a test partition.

First create the mount directory
```
mkdir /home/pippo/tmpmnt
```Then edit your /etc/fstab to include a line to mount the ext3 partition
```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```This is the line I used (modified to fit your specs)
```
/dev/hda1 /home/pippo/tmpmnt ext3 defaults 0 0
```Then save, exit and remount the partitions
```
sudo mount -a
```Then take ownership of the mount folder, and allow full permissions
```
sudo chown pippo.pippo -R /home/pippo/tmpmnt
sudo chmod 777 -R /home/pippo/tmpmnt
```Then if the partition is unmounted and remounted the ownership/permissions remain the same.

---

### Post by knalle on 2006-02-19
i was thinking of

mount -o rw

---

### Post by knalle on 2006-02-19
g

---

