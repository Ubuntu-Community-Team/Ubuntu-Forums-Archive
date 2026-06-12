---
title: "looking for a sandra like prog for linux"
date: 2008-09-05
forum: Hardware
---

### Post by georgegerm on 2008-09-05
is there a progy out there that can tell me whats the size of my disk, in simple terms..??
disk usage says i have a 120 but i bought a dell with a 80 disk..
if disk usage is right i am lucky but i do not think so...
and going that way is there any sys sandra or everest for linux like progy out there???t what commands should i use if there is none..
slow i am a newby
thank you:guitar:

---

### Post by Hellkeepa on 2008-09-06
HELLo!

Write "df -h" in a terminal window. ;-)
However, it should be noted that this function is just a fraction of what SiSoft Sandra actually does. So the title of the thread isn't quite in sync with the question you're asking.

Happy surfin'!

---

### Post by georgegerm on 2008-09-06
jorge@jorge-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              55G  6.3G   46G  13% /
varrun                1.4G  236K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G   60K  1.4G   1% /dev
devshm                1.4G   48K  1.4G   1% /dev/shm
lrm                   1.4G   39M  1.4G   3% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       55G  6.3G   46G  13% /home/jorge/.gvfs

so please tell me what is the size of my plate etc :guitar:
and thanks

---

### Post by 2damncommon on 2008-09-06
You want to install "lshw" and "lshw-gtk".
The GUI version seems to prefer to be started with "sudo lshw-gtk" in a terminal.

---

### Post by Hellkeepa on 2008-09-06
HELLo!

Ah, a slight misunderstanding of your question I see.

This should give you all the info you need on the hard drives.
```
$ sudo -i
$ fdisk -l
```
Note that the partition size is shown as blocks, not bytes, and that the GB size for the entire drive is base 10. (That means 1000 MB = 1 GB, not 1024 MB = 1 GB.)

Happy codin'!

---

### Post by 2damncommon on 2008-09-06
I need to modify my answer.

lshw gives lots of system information including disk information.

gparted gives better disk information. After installing "gparted" you should find partition editor under System -> Administration.

---

### Post by georgegerm on 2008-09-06
thanks a million for all ur ubu help ,,
you guys are great

---

### Post by Hellkeepa on 2008-09-06
HELLo!

You're welcome. :)

Happy codin'!

---

