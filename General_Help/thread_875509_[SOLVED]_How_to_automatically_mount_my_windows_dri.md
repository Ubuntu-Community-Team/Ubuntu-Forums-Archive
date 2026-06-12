---
title: "[SOLVED] How to automatically mount my windows drive at boot time?"
date: 2008-07-30
forum: General Help
---

### Post by MaxMax on 2008-07-30
I have Ubuntu 8.04, dual boot with XP. I can easily mount my windows drive through the menu "Places / 76.9 GB Media". I am looking for a way to have it automatically mounted when Ubuntu starts up. Any suggestions? Thanks! -- MaxMax

---

### Post by SpenceMakesSense on 2008-07-30
I know this doesnt help very much. But see if there is some kind of terminal command that mounts it then add it to the session udner system prefferences

---

### Post by MaxMax on 2008-07-30
That is a good thing to know... Now all I need is the terminal command :)

---

### Post by Separ on 2008-07-30
I'm thinking add a line to /etc/fstab. Ill go do some research :)

---

### Post by pcozzy on 2008-07-30
u need to edit sudo gedit /etc/fstab 
u need to put a line similar to this:
```
/dev/sdb1  /media/Windows_Drive  ntfs-3g users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
```
I say similar because you should be consistent with other entries in fstab and make sure that you have a 0 0 at the end don't use 0 1 or 0 2. 
here is a link that explains the function and use of fstab:
[http://en.wikipedia.org/wiki/Fstab]("http://en.wikipedia.org/wiki/Fstab")

I forgot sudo mkdir /media/Windows_Drive before restarting.

---

### Post by Separ on 2008-07-30
Ack, pcozzy beat me to it :D

To figure out what to replace "/dev/sdb1" with, post the output of
```
sudo fdisk -l
```

---

### Post by munkyeetr on 2008-07-30
A couple of things you need to do:

1) Find out which device your xp drive is on by typing
```
blkid
```
in the terminal. The device will be /dev/sdaX or similar

2) Create a directory to use as the mountpoint for the drive 
```
sudo mkdir /media/winxp
```

3) Edit your /etc/fstab file to mount it when the system boots
```
gksudo gedit /etc/fstab
```

Add the following line, replace /dev/sdaX with the proper device as you found with blkid:
```

/dev/sdaX /media/winxp ntfs defaults 0 0

```

Next time you boot, it should be mounted.

---

### Post by MaxMax on 2008-07-30
output of sudo fdisk -l 

-=-=-=-=-=-

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        9353    75063712+   7  HPFS/NTFS
/dev/sda3            9354        9725     2988090   db  CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dab0dab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19270   154786243+  83  Linux
/dev/sdb2           19271       19457     1502077+   5  Extended
/dev/sdb5           19271       19457     1502046   82  Linux swap / Solaris

-=-=-=-=-=

---

### Post by Separ on 2008-07-30
Replace /dev/sdb1 with /dev/sda2 then :)

---

### Post by SuperSonic4 on 2008-07-30
I'd just install ```
ntfs-configuration tools
``` from the repos and run it

---

### Post by shazbut on 2008-07-31
I found this...

[http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html](http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html)

...to be the most painless way for me.  Seems to change the default behaviour back to how it was in versions < 8.04.  Hope it helps.

---

### Post by MaxMax on 2008-07-31
Thank you everyone!!! All this help is much appreciated! -- MaxMax

---

