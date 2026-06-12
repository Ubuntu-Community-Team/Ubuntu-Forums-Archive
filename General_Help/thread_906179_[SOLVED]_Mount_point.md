---
title: "[SOLVED] Mount point"
date: 2008-08-31
forum: General Help
---

### Post by wfp on 2008-08-31
Ok so i wanted to dual boot ubuntu with kubuntu lol . So half way through the kubuntu install  my system just freezes. Now when i open gparted i have this showing up /dev/sda6 which has 23Gigs of free space with 400mbs being used i figure thats part of kubuntu install that did not take. Any way i want to mount /dev/sda6 so i can use the free space. gparted is not giving me that option,and when i try in the terminal i get error> sudo mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab I can not continue the install because my cdrom drive is on the blinkers again. # /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# 
/dev/sda1
UUID=066ac81e-d42c-4602-9c82-37524bc12c9f /               ext3    relatime,errors=remount-ro 0       1

 /dev/sda5
UUID=b2985951-e96d-4bb8-bba4-323f348f80fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Too Late on 2008-08-31
You can manually mount it without /etc/fstab, but then you have to specify the mounting point, eg.
```
sudo mount /dev/sda6 /mnt/mountingpoint
```
Note that the mounting point directory must exist before mounting. To create it, type:
```
sudo mkdir /mnt/mountingpoint
```
(Of course, the mounting point directory can be named anything you like.)

You can add it to /etc/fstab file, too (again, you must make the mounting point directory yourself). Add these lines to the fstab file (the first line is just a comment, not mandatory):
```
# /dev/sda6
/dev/sda6 /mnt/mountingpoint ext3 relatime 0 2
```
(Assuming that the filesystem is ext3.)

Alternatively, you can replace the /dev/sda6 with the UUID. To find the correct UUID for that partition, type:
```
sudo blkid
```
The the corresponding fstab line should look like this:
```
# /dev/sda6
UUID=12345678 /mnt/mountingpoint ext3 relatime 0 2
```

To edit the fstab file, type:
```
gksudo gedit /etc/fstab
```

---

### Post by wfp on 2008-08-31
thanks for the reply will try tomorrow need to get some sleep.

---

### Post by wfp on 2008-09-03
Thanks everything went smooth on the second try the first try i put the uuid in wrong, and well that scared me when i booted had a black screen. Second time was a charm took your advise created a mounting point directory and then added everything to my /etc/fstab it's showing up, thanks, but was wondering if someone can show me how to apply read and write permissions for myself to the new partition.

---

### Post by Too Late on 2008-09-03
You can take the ownership of that partition by typing:
```
sudo chown wfp: /mnt/mountingpoint
```
, where wfp is your username (the colon automatically changes the group, too) and the last part is the full path to the mounting point.

---

### Post by wfp on 2008-09-03
Great Thanks.

---

