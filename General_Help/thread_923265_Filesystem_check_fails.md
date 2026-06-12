---
title: "Filesystem check fails"
date: 2008-09-18
forum: General Help
---

### Post by wersdaluv on 2008-09-18
Whenever my computer does a filesystem check, on the GUI usplash, it is stuck at 70% then after a while the terminal will appear and it will say that the filesystem check failed.

My computer works properly, though. Any idea on how to fix this?

---

### Post by jigsaws on 2008-09-18
Follow the instructions and fcsk this filesystem manually.

---

### Post by wersdaluv on 2008-09-18
> **jigsaws said:**
> Follow the instructions and fcsk this filesystem manually.
Can I fsck it manually without waiting that long again for the CLI after the usplash?

---

### Post by Nepherte on 2008-09-18
You could disable the fsck on startup for that partition/disk in /etc/fstab.

Open up /etc/fstab:
```
gksudo gedit /etc/fstab
```
and find the line of the partition that is giving errors. An example from my fstab:
```
UUID=6E22-A265          /media/MyBook   vfat    auto,users,uid=1000,gid=100,dmas
k=027,fmask=137 0       **1**
```
and change it to:
```
UUID=6E22-A265          /media/MyBook   vfat    auto,users,uid=1000,gid=100,dmas
k=027,fmask=137 0       **0**
```

You can manually check the partition if you have it unmounted. So first unmount it before you run fsck in the terminal. You might want to use the -V option in fsck for a verbose mode so you can see what's happening. I wouldn't just ignore the fact that it's stuck at 70%. It's probably a corrupted file system or a soon dead hard disk.

---

### Post by wersdaluv on 2008-09-18
> **Nepherte said:**
> You could disable the fsck on startup for that partition/disk in /etc/fstab.

Open up /etc/fstab:
```
gksudo gedit /etc/fstab
```
and find the line of the partition that is giving errors. An example from my fstab:
```
UUID=6E22-A265          /media/MyBook   vfat    auto,users,uid=1000,gid=100,dmas
k=027,fmask=137 0       **1**
```
and change it to:
```
UUID=6E22-A265          /media/MyBook   vfat    auto,users,uid=1000,gid=100,dmas
k=027,fmask=137 0       **0**
```

You can manually check the partition if you have it unmounted. So first unmount it before you run fsck in the terminal. You might want to use the -V option in fsck for a verbose mode so you can see what's happening. I wouldn't just ignore the fact that it's stuck at 70%. It's probably a corrupted file system or a soon dead hard disk.

Woah! Here's my fstab. I don't know what to do from here...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7b4677ba-295e-4aa5-80c9-7024fc5aaefa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=267cd70d-1167-4c1c-9018-803face52fae /home           ext3    relatime        0       2
# /dev/sda5
UUID=ee96c733-b598-477c-99d4-93b772c59b0c /mnt/sda5       ext3    relatime        0       2
# /dev/sda4
UUID=48C2-A001  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=4bf2c1b7-2cb2-435c-a9f7-de9a5db59280 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Nepherte on 2008-09-18
Well, what drive is fsck checking (it should be saying that during usplash)?
Most likely in the form of /dev/sdxx where the first x is a character and the second one a number.

---

### Post by wersdaluv on 2008-09-18
I can't boot my Ubuntu Hardy now. I also already did fsck -V. Thank goodness, I have a Windows partition. hehe

---

### Post by Nepherte on 2008-09-19
You did unmount the drive before the fsck right? Not unmounting might mess up a lot, but I guess you did since fsck gives you a warning if you want to do so. I  guess we don't have to figure out the problem disk anymore as your / partition doesn't want to boot anymore. Maybe you can still rescue some of it running a live cd if you need to.

---

### Post by wersdaluv on 2008-09-19
I did fsck without unmounting it and had a lot of trouble. Just reformatted so it's fine now. haha

---

### Post by Nepherte on 2008-09-19
Then remember to unmount it in the future. Using the mounted partition while fsck tries to fix the filesystem is a really bad idea, hence the warning the program spits out.

---

### Post by wersdaluv on 2008-09-20
Yep! Thank you, dude! :)

---

