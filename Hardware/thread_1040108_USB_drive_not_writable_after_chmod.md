---
title: "USB drive not writable after chmod"
date: 2009-01-15
forum: Hardware
---

### Post by update_manager on 2009-01-15
I can't seem to get my USB key to be writable by anyone other than root on an Ubuntu server installation. Any advice? 

sudo mount /dev/sdd /mnt/KINSTON/ -t vfat

ls -alh /mnt/KINSTON/
total 1.2G
drwxr-xr-x 2 root root 4.0K 1969-12-31 19:00 .
drwxr-xr-x 3 root root 4.0K 2009-01-15 07:54 ..
-rwxr-xr-x 1 root root 650M 2009-01-10 16:22 file1
-rwxr-xr-x 1 root root 286M 2009-01-10 16:22 file2
-rwxr-xr-x 1 root root 201M 2009-01-10 16:08 file3.7z

sudo chmod 777 /mnt/KINSTON/
sudo chmod 777 /mnt/KINSTON/*

ls -alh /mnt/KINSTON/
total 1.2G
drwxr-xr-x 2 root root 4.0K 1969-12-31 19:00 .
drwxr-xr-x 3 root root 4.0K 2009-01-15 07:54 ..
-rwxr-xr-x 1 root root 650M 2009-01-10 16:22 file1
-rwxr-xr-x 1 root root 286M 2009-01-10 16:22 file2
-rwxr-xr-x 1 root root 201M 2009-01-10 16:08 file3.7z

---

### Post by update_manager on 2009-01-15
sudo mount /dev/sdd1 /media/KINGSTON/ -t vfat -o uid=user

---

