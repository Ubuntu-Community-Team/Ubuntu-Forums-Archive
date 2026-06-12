---
title: "changing root partition label"
date: 2008-08-31
forum: General Help
---

### Post by myusername on 2008-08-31
im running lxde and on the side pane of pcmanfm my root partition is called 99.3 GB Volume. is there anyway i could rename this without destroying data or reinstalling?

edit: btw the filesystem is jfs

---

### Post by plucky on 2008-08-31
> **myusername said:**
> im running lxde and on the side pane of pcmanfm my root partition is called 99.3 GB Volume. is there anyway i could rename this without destroying data or reinstalling?

edit: btw the filesystem is jfs


From [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

JFS:
Use jfs_tune:
Code:

jfs_tune -L <Label> <device>

To show the label:
Code:

jfs_tune -l <device>

    Note:That is a small "L" and not the number 1.



Good Luck

---

### Post by myusername on 2008-08-31
im supposed to do that in the form of jfs_tune -L <Label> /dev/sda6 right?
well i dont think it worked here is what it said:
$ sudo jfs_tune -L Arch /dev/sda6
jfs_tune version 1.1.12, 24-Aug-2007

/dev/sda6 is mounted.
While mounted, the only supported jfs_tune parameter is -l.

its my ROOT filesystem...so maybe i could do it from a livecd but im running arch and i dont want to screw something up

---

### Post by myusername on 2008-09-01
*bump*

---

### Post by Zorael on 2008-09-01
Yes, do it from a live cd/usb environment, should be safe as long as you don't tinker about.

---

