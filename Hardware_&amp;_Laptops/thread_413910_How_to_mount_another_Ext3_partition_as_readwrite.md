---
title: "How to mount another Ext3 partition as read/write?"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Mazza558 on 2007-04-19
I'm trying to allow read/write access to another Ext3 partition, but I only get read access. This is extremely annoying, as I want to use this partition for documents/media. I didn't select this partition to be used for anything during the install.

I've tried

```
 sudo mount -t ext3 -o rw /media/sda2 /media/sda2

```

to try and reconfigure the drive to be read and write, likewise with

```
sudo mount -t ext3 -O defaults /dev/sda2 /media/sda2
mount: /dev/sda2 already mounted or /media/sda2 busy
mount: according to mtab, /dev/sda2 is already mounted on /media/sda2

```

So I cannot change permissions this way. Help! :(

---

### Post by Mazza558 on 2007-04-19
Anyone?

---

### Post by Mazza558 on 2007-04-19
Surely someone knows what to do?

---

### Post by Mazza558 on 2007-04-19
I've figured it's to do with permissions....

I've somehow managed to give some files/folders full read and write permissions, but others are still locked. How do you give a whole drive read/write permissions? :)

---

### Post by Austin_KW on 2007-04-19
"sudo mount" is going to mount the disk as root with owner=root. Add an entry to the fstab with options "noauto" to not automatically mount and "users" to allow normal users to mount the disk.
Then you can use the mount command without the 'sudo' and you will be the owner.

---

### Post by patrickfromspain on 2007-04-20
I have some ext3 partitions and to make them full read/write I do: sudo chmod 777 -R /media/sda2

---

### Post by H.E. Pennypacker on 2007-04-22
> **patrickfromspain said:**
> I have some ext3 partitions and to make them full read/write I do: sudo chmod 777 -R /media/sda2

Worked for me.

---

