---
title: "I don't own my hard drive?? drive permissions"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by David Grant on 2005-05-20
I mounted several drives during the install, and subsquently it says root is the owner for all, so I have read only acesss (I need to read/write). I want full acess to the drives....how do I do this?

---

### Post by Xian on 2005-05-20
[QUOTE=David Grant]I mounted several drives during the install, and subsquently it says root is the owner for all, so I have read only acesss (I need to read/write). I want full acess to the drives....how do I do this?[/QUOTE]
If you can post the contents of your /etc/fstab file we can assist you in this.

```
$ sudo gedit /etc/fstab
```

---

### Post by David Grant on 2005-05-20
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hdc1       /windows        vfat    defaults        0       0
/dev/hda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0


all show up as owned by root. (only my usb flash drive shows up as reeper my user account, when plugged in)

---

### Post by Xian on 2005-05-20
[QUOTE=David Grant]all show up as owned by root. (only my usb flash drive shows up as reeper my user account, when plugged in)[/QUOTE]
Okay, your hda3 is fine with root-only permissions.
The hda2 is fine as well (just a swap partition).

Change your fstab line for that FAT partition to this:

```
/dev/hdc1 /windows vfat rw,user,uid=1000,gid=1000,umask=0000 0 0
```
It appears to be overkill but it should work in most cases.
The scd0 looks to be okay. Any issues with that mounting?

---

### Post by David Grant on 2005-05-21
Thanks, got it working

---

### Post by faixan on 2008-02-11
i'm having this very same problem... but with less complications, i can read write, but the problem comes when i try to share folders on my network it says "Access Denied you do not have the permission" but still it opens the sharing tab and shares the whole drive rather than the folder, 
i checked the permissions tab in folder properties it shows...
Owner: root
group : plugdev
text view:drwxrwx---
rest of the options are disabled...
here's my fstab content..
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=aa8764ed-2ba3-4f5a-bf37-936c91eb9d31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ACC3-B354  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=007B-91F1  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=F86D-CE90  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=d75e68f3-1d2a-4914-873e-387e3f654e7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

what should i do?!

---

### Post by Yellow Pasque on 2008-02-11
Are you a member of the plugdev group?
```
sudo gedit /etc/group
```

---

