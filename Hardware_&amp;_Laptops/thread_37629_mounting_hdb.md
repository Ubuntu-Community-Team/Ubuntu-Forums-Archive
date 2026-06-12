---
title: "mounting hdb"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by boilertech on 2005-05-27
On hdb I have Mandrake installed. I need to get files off this drive but I cannot access. It is listed in /dev as a drive. How do I get access?

---

### Post by Kyral on 2005-05-27
Make a mountpoint with mkdir then add an entry in /etc/fstab

The mount it

---

### Post by crane on 2005-05-27
[QUOTE=Kyral]Make a mountpoint with mkdir then add an entry in /etc/fstab

The mount it[/QUOTE]

Yep just make a directory for mounting it. Say something like ~/manny
then add a line to your fstab something like:

/dev/hdb	/home/you/manny ext3	rw,exec		0	0

*fstab is located at /etc/fstab ;-)

---

### Post by mohaham on 2005-05-27
to mount..
sudo mkdir /media/mandrake
sudo mount /dev/hdb1 /media/mandrake -t ext3 -o umask=000


to unmount..
sudo umount /media/mandrake

or you can add this line to the  /etc/fstab  file to mount on boot up
/dev/hdb1       /media/mandrake  ext3    umask=000       0       0

assumptions:
hdb1  - mandrake partition
ext3   - filesystem type

---

### Post by boilertech on 2005-05-28
This worked editing /fstab
dev/hdb5        /media/mandrake     ext3    rw,exec     0       0

Thanks ALOT this distro and you people helping rock. \\:D/

---

