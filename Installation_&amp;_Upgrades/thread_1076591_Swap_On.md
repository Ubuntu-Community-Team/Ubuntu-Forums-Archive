---
title: "Swap On"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by LIB53 on 2009-02-21
I needed more swap space so i booted up partedmagic Live and enlarged my swap. Now it doesn't turn on automatically. I have to open the partition editor and right click>Swapon. sudo swapon -a give me this error message:

swapon: cannot canonicalize /dev/disk/by-uuid/e9a66793-b4f7-4c37-b127-d624beaccdeb: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/e9a66793-b4f7-4c37-b127-d624beaccdeb: No such file or directory

I need a way so that my swap turns on automatically.

---

### Post by dje on 2009-02-21
please post the output of:
```
sudo blkid
cat /etc/fstab
```

---

### Post by LIB53 on 2009-02-21
akil@Krishnan:~$ sudo blkid
/dev/sda1: UUID="86F8AEC4F8AEB23B" TYPE="ntfs" 
/dev/sda5: UUID="dfce7dd7-4988-4b32-86e0-75f85448493c" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5fae6323-4473-407f-9574-0a30d2784684" 
/dev/sdb1: UUID="58C4402FC44011A4" LABEL="FreeAgent Drive" TYPE="ntfs" 


akil@Krishnan:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=dfce7dd7-4988-4b32-86e0-75f85448493c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e9a66793-b4f7-4c37-b127-d624beaccdeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by dje on 2009-02-21
ok, this is a simple fix :). What happened was when you resized the swap partition its UUID was changed so when you boot the system it tries to turn a non existent swap partition on. To fix it simply open up fstab:
```
gksu gedit /etc/fstab
```
replace the highlighted red text below with the blue text and save and close the file

> **LIB53 said:**
> akil@Krishnan:~$ sudo blkid
/dev/sda1: UUID="86F8AEC4F8AEB23B" TYPE="ntfs" 
/dev/sda5: UUID="dfce7dd7-4988-4b32-86e0-75f85448493c" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="[COLOR="Blue"]5fae6323-4473-407f-9574-0a30d2784684[/COLOR]" 
/dev/sdb1: UUID="58C4402FC44011A4" LABEL="FreeAgent Drive" TYPE="ntfs" 


akil@Krishnan:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=dfce7dd7-4988-4b32-86e0-75f85448493c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=[COLOR="Red"]e9a66793-b4f7-4c37-b127-d624beaccdeb[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

hope that helps,
dje

---

### Post by LIB53 on 2009-02-21
Thanks, it worked. That was a really quick reply btw. I was expecting a reply an hour later or something. Thanks again.

---

### Post by ddmdllt on 2009-02-21
Don't hesitate to edit the title to mark your post as resolved ;)

---

### Post by LIB53 on 2009-02-21
And how do i edit the title? I'm sorry, but i'm very new to this forum. It's a bit different.

---

