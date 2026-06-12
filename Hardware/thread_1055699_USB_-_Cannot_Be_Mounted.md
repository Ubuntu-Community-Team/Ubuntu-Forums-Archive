---
title: "USB - Cannot Be Mounted"
date: 2009-01-31
forum: Hardware
---

### Post by wordslinger on 2009-01-31
I noticed that there are so many problems with those who are unable to mount their USB Disk on Ubuntu 8.04.2. The message that pop up was: *"Invalid mount option when attempting to mount the volume"*. 

Here is a solution that I came across while surfing the web for more than 3 hours.

Step 1: Remove your USB/Flash Disk from your PC/Notebook/Netbook.

Step 2: Go to Applications > Accessories > Terminal and run the following command: **[sudo gedit /etc/fstab]**

Step 3: In the file you opened, you probably find a line like this:
**[/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0]**

Step 4: Comment it by adding a "#" like this:
**#/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0**

Step 5: Plug in your USB/Flash Disk again.

I hope this is of some help for those who need it.

Cheers!

---

### Post by Levitation on 2009-04-30
Thank you! Wow! Amazing! So simple!

BTW: There were two similar lines:

#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

As you can see, I added # to each. Is this okay? It works...

---

### Post by epswinde on 2009-04-30
Remember: if you want to put a cd/dvd into your optical drive, you will have to uncomment this line.

And also, instead of using: 
```
 sudo gedit /etc/fstab 
```
use:
```
gksudo gedit /etc/fstab 
```

Indeed, it is wise to use gksudo instead of sudo when launching any gui application with root privileges.

---

