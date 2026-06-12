---
title: "How do I install a second hard drive?"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by Maheriano on 2006-07-15
I'm lost without the Konsole. I kept my backup hard drive unhooked during install, I didn't want to chance accidentally partitioning it. Now I have it hooked up and when I try to access it, I get an error saying it can't be mounted. Here's the error ```
error: device /dev/hdc3 is not removable

error: could not execute pmount
```

And here's my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

So I guess I have to add it in there (hdc3), but what are the other options?

---

### Post by rmjb on 2006-07-16
The other options follow the same structure:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>  <dump>  <pass>
proc            /proc           proc    defaults     0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw           0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto  0       0
[COLOR="Red"]/dev/hdb3       /mnt/winC       vfat    defaults     0       0[/COLOR]
```

Where [COLOR="Red"]/mnt/winC[/COLOR] is your intended mount point and [COLOR="Red"]vfat[/COLOR] is the file system format of your other drive. If these things are different, enter the correct values.

- rmjb

---

### Post by Maheriano on 2006-07-16
I cloned what I had on another Gentoo setup and had > /dev/hdc3       /mnt/hdc3       auto    noauto,users        0       0


The only problem is now it's telling me the /mnt/hdc3 mount point doesn't exist. Which is true, there's nothing in the /mnt folder at all. I've restarted with the......wait, I plugged in the IDE cable and not the power cable. I'm a moron. Let me try that first.

---

### Post by Maheriano on 2006-07-16
Nevermind, I had power going to it the whole time. So I've restarted with the hard drive hooked up, and when I check the /mnt folder, there's nothing in there. Nothing at all. And you can see above what I've added to my /etc/fstab file.

---

### Post by Maheriano on 2006-07-16
And now I get a new error message.
> mount: mount point /mnt/hdc3 does not exist



---

### Post by Orpheus- on 2006-07-16
> **Maheriano said:**
> And now I get a new error message.

You need to create the mount point.

sudo mkdir /mnt/hdc3

---

### Post by Maheriano on 2006-07-16
haha......duh......
Ya it worked!

---

