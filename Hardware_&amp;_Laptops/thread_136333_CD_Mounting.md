---
title: "CD Mounting"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by R3linquish3r on 2006-02-25
Well this is my second install of kubuntu after windows (once again) got screwed over and the install of windows screwed over my booting of kubuntu. Before I had to reformat, whenever I put a cd in one of my 2 drives, or both, they would mount automatically and I would also get a shortcut on my desktop to the contents of them. Now I have to mount them manually and go through the directories to get to the contents. I'm guessing this was a setting I setup myself with some HOWTO on here last time but I can't find it. Anyone know what I need to do?

---

### Post by taurus on 2006-02-25
It should be in /etc/fstab...

```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by R3linquish3r on 2006-02-25
ya theyre both in there...... i jsut dontt get why theyre not auto booting.

also another wone if u care to take a swing at it.... i have to keep ocnfigureing my wireless conection every time i boot it wont stay configured like in my last install.....

---

### Post by R3linquish3r on 2006-02-25
hey this is kinda weird to. when I do a mount-a I get this error:

```
ed@ubuntu:~$ sudo mount -a
mount: No medium found
mount: No medium found

```

---

### Post by R3linquish3r on 2006-02-25
for some reason now the cd im trying to put in jsut flat out wont mount. im really stuck in a rut here.

---

### Post by R3linquish3r on 2006-02-25
bumps....

still need help whoever has an idea........

---

### Post by taurus on 2006-02-25
Do you mean it won't automount or won't mount by hand???

---

### Post by R3linquish3r on 2006-02-25
before it ownt auto mount. but now it wont mount by hand either.

here is my fstab if u need it:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222  0       0
/dev/sda1       /media/sda1     vfat    iocharset=utf8,umask=000        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2006-02-25
What kind of CD is it and how did you mount it, the command?

---

### Post by R3linquish3r on 2006-02-26
Its my Quake 3 CD (I'm having trouble with that too but I posted in another thread) And I'm trying to mount it by just doing sudo mount -a.

---

