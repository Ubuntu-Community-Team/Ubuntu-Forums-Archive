---
title: "Mounting a fat32 partition in Ubuntu"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by sent17inel on 2007-02-18
I have a 60 Gig hard drive. I would like to mount a fat32 partition in linux. Heres all my info i tried to get as much as i could find but im not sure if this is even the right info.. Im a linux newb.  My 60 gig hard drive is divided as follows.... 27.95 Gigs is for my windows xp and its called /dev/hda1   ,next i have  3.91 Gigs and thats for my fat32 which has nothing on it yet but i would like to be able to transfer files between windows and linux using this partition and this is called /dev/hda2  and my ubuntu is on a 23.42 Gig partition and is called  /dev/hda3... also there is a /dev/hda4 extended and a /dev/hda5 linux swap.... can someone please tell me how to mount my fat32 drive... i need extremely specific directions cuz i barely understand the linux file structure... but i must admit this file structure is cool...

---

### Post by yabbadabbadont on 2007-02-18
Add a line to your /etc/fstab that looks something like this:

```
/dev/hda2       /media/windata      vfat         defaults,utf8,umask=007,gid=46  0       1
```
You will need to create the /media/windata directory first.

---

### Post by sent17inel on 2007-02-18
ok i can do that i think.. but how would i create the directory?

---

### Post by yabbadabbadont on 2007-02-18
Are you sure that Ubuntu didn't already add entries for your windows drive?  It usually does if it detects windows installed on the machine when you installed Ubuntu.  Just to be safe, please post the contents of your /etc/fstab file.  Also, post the output of the following command: "sudo fdisk -l"  (don't include the quotes when you run it)

---

### Post by sent17inel on 2007-02-18
Muahahahhahahhaha..... Im SOOOO HAPPPY...... It mounted ur so awesome!!! I feel like such a newb for asking how to create the windata directory thing... I just went to media and then created a folder called windata... and then i saved the line that u told me to write and i rebooted and it loaded!!!! mUAHAHAHAH im SOOOO HAPPPPYYYY thank you soooo much dude.... This problem was bothering me for days....

---

