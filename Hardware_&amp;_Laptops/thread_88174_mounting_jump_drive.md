---
title: "mounting jump drive"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by cbeshears on 2005-11-09
I am new to Linux and an trying to learn how to mount my jump drive through the command line interface.  I have read the manual (using "man mount") and have done online searches for help but can't figure out what I'm doing wrong.  

I have also entered "mount" to see the available devices.  The device is listed as "/dev/sdf1 /media/CHRISTOPHER".

I have entering the following; however, I'm not even sure if the command is right:

```
"mount -t msdos /dev/sdf1 /media/CHRISTOPHER"
```

When I type that in it tells me "special device /dev/sdf1 does not exist"

Any suggestions?  Any help is appreciated.

---

### Post by ssam on 2005-11-09
first off if it shows up when you run
```
mount
```
then it is already mounted.

you could use
```
umount /dev/sdf1
```
to unmount it first (it is **u**mount not **un**mount)

if the device was previously labled /dev/sdf1 that is no guarenty that it currently has that label. you can run
```
dmesg
```
after pluggin it in to see what label it has been given.

edit
and also you will probably need to preceed the mount and umount commands with sudo, ie
```
sudo mount /dev/sdf1
```
to get root priviliges

---

### Post by cbeshears on 2005-11-09
Great!  It appears that I'm able to umount and mount but don't understand how to list the contents of the drive.  When I enter ```
ls
```nothing appears.  There should be a directory and a file inside of it.  Also my shell prompt doesn't change when I mount my jump drive.  Is it suppose to?

---

### Post by ssam on 2005-11-09
you may have to change directory to the drive.
```
cd /media/CHRISTOPHER
```
then
```
ls
```
or just
```
ls /media/CHRISTOPHER
```
to list the contents without moving there

if you are very new to the command line you should probably search for a tutorial.

---

### Post by cbeshears on 2005-11-09
I will.  Thank you so much for your help.

---

### Post by ssam on 2005-11-09
no problem.

have fun

---

