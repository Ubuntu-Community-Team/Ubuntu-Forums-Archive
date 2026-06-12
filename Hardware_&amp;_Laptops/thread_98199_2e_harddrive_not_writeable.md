---
title: "2e harddrive not writeable"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by Blaauw01 on 2005-12-02
good evening,

I have a second haddrive where i have got the problem that i am not able to get the permission in Ubuntu 5.10 to get as user the right to write on this harddrive. I have changed the /etc/fstab with the following line:
/dev/hdb5 /mnt/hdb vfat users,gid=users,umask=0002, 0 0

I am only able to write as root. I have tried to change the owner of the folder ( as root) but also denied. with command : chown username /location-of-folder.

any suggestions

---

### Post by Mr. Swiveller on 2005-12-03
Have you already checked whether the drive is marked as writable? 

I am not sure about Ubuntu, but in Kubuntu (which uses the K graphical environment) you can view and modify permissions for each of your harddrives if you launch 'Disk & Filesystems' from settings:/System/.

Swiveller

---

### Post by doitashimashite on 2005-12-03
In /etc/fstab, change this line

/dev/hdb5 /mnt/hdb vfat users,gid=users,umask=0002, 0 0

into

/dev/hdb5 /mnt/hdb vfat noauto,user,uid=<your user id>,gid=users

Then remount /mnt/hdb.

This should work!

---

### Post by Blaauw01 on 2005-12-03
Thank you for this wise lessons, after days of hard work and a lot of .......... the change in the /etc/fstab did the job.

thanks:D

---

