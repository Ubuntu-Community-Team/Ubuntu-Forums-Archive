---
title: "unable to access cdrom"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by dodgeman79 on 2007-08-26
i just installed FF 7.04 and can't access any CD inserted into the drive.  I'm trying to do some updates and it wants the install CD.  Every time I try and access the drive it tells me;
```
unable to mount media
there is probably no media in the drive
```

I know everything works I just used the same CD to install FF 7.04.

here is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=78a35a32-fee7-4348-998c-2eb5cb00e393 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=302e7c5f-5443-4858-bf0a-40064e307933 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by sam81 on 2007-08-26
the fstab line for the cd is the same as mine, looks fine

what happens if you try to mount manually:

cd ~/
mkdir flash
sudo mount -t iso9660 /dev/scd0 /home/your_username/flash

then go to the directory "flash", and see whether the cd appears

if have an internet connection you can disble the cd from the repositories by the way, in synaptic go to "Settings" -> "Repositories" and unceck the cd entries

---

### Post by dodgeman79 on 2007-08-26
i just rebooted with a cd in the drive and I can see the icon on my desktop and access it if I double click it.

here is the output
```

baker@ubuntu:~$ mkdir flash
baker@ubuntu:~$ sudo mount -t iso9660 /dev/scd0 /home/baker/flash
Password:
mount: block device /dev/scd0 is write-protected, mounting read-only
baker@ubuntu:~$ 

```

after running the code I can still access the CD just fine.  I'll try to reboot with out the cd and see if I can get it to come back up.

---

### Post by dodgeman79 on 2007-08-26
i thought it was working.  I'm trying to install ndiswrapper and it wants the CD.  I have two regular and one alt CD, and none are the CD that it's asking for.  I do get an error message after a few failed attempts.
```
W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb
```

---

### Post by Doug11 on 2007-08-26
Im having the same problem, cannot mount dvd-drive, medium not inserted. And my fstab is the same.

---

### Post by dodgeman79 on 2007-08-26
i hae rebooted a few time and have lost min again.  I'll try some more and post if I find anything useful

---

### Post by dodgeman79 on 2007-08-27
if I have a CD in the drive and boot up I can switch it out three times before I loose the CD drive.  if I don't have one in during boot i can't get to it at all.

if I try the method from the previous posts i get
```
baker@ubuntu:~$ mkdir flash
baker@ubuntu:~$ sudo mount -t iso9660 /dev/scd0 /home/baker/flash
Password:
mount: special device /dev/scd0 does not exist
baker@ubuntu:~$ 
```

if I try to mount/unmount from the File Browser or Terminal
```
Unable to mount the selected volume.
mount: special device /dev/scd0 does not exist
```

current fstab.  I set the CD drive to auto and it went back to noauto after reboot.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=78a35a32-fee7-4348-998c-2eb5cb00e393 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=302e7c5f-5443-4858-bf0a-40064e307933 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto  0       0
```

---

