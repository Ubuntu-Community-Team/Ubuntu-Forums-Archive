---
title: "fsck won't start automatically at start up"
date: 2008-09-09
forum: General Help
---

### Post by andlinux on 2008-09-09
I'm running Ubuntu 8.04 and normally when I boot my system then fsck will start after 30 boot times. The problem is that it's been a very long time since fsck started, so it's not working anymore.

How can I fix this so that it will check my filesystem after 30 boot times ?

---

### Post by eggdeng on 2008-09-09
Try
```
sudo tune2fs -c 30 /dev/sda1
```
Change sda1 to whichever is the disk or partition you want checked. Use ```
df
``` to get the list. You can set some small number instead of 30 to check if it works.

---

### Post by andlinux on 2008-09-09
Ok, I will try that. :)

---

### Post by andlinux on 2008-09-09
Well, I took 1 instead of 30 but it's still not working.

When I look in the log files I see this:

[   32.221517] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended

---

### Post by dannyboy79 on 2008-09-09
what does your /etc/fstab file look like. if you have zero's at the end of each line fsck won't check them. At least that's my understanding of reading the man page for fstab.

---

### Post by andlinux on 2008-09-10
> **dannyboy79 said:**
> what does your /etc/fstab file look like. if you have zero's at the end of each line fsck won't check them. At least that's my understanding of reading the man page for fstab.
Sorry for the late reply but here's my fstab file:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=de2c171d-43ee-49e5-8f3f-b81f2cfac681 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1040d695-8bdb-40f6-90ba-4623418725df none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

# usbfs is the USB group
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

---

### Post by dannyboy79 on 2008-09-12
> **andlinux said:**
> Sorry for the late reply but here's my fstab file:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=de2c171d-43ee-49e5-8f3f-b81f2cfac681 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1040d695-8bdb-40f6-90ba-4623418725df none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

# usbfs is the USB group
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```
it looks like ok to me, not sure what else to tell you. sorry

---

### Post by LittleKoy on 2008-09-12
My question is a bit different, but still on fsck: if I do

```
sudo fsck /
```

it tells me:

```
fsck 1.41.0 (10-Jul-2008)
e2fsck 1.41.0 (10-Jul-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

```

What should I do to run a fsck?

---

### Post by Nepherte on 2008-09-12
You have to unmount the disk first before you can run a check on it.

---

### Post by dannyboy79 on 2008-09-12
> **LittleKoy said:**
> My question is a bit different, but still on fsck: if I do

```
sudo fsck /
```

it tells me:

```
fsck 1.41.0 (10-Jul-2008)
e2fsck 1.41.0 (10-Jul-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

```

What should I do to run a fsck?
you'll have to run fsck from a livecd that doesn't mount your / (root) partition. Otherwise, no matter what your / partition is always going to get mounted if you run ubuntu which is installed on your computer. You will not be able to unmount / because it's in use by the system.

Maybe someone else will come along and be able to figure out why fsck isn't running when it should be. Have you tried a search within the forum or goggle?

---

### Post by kostkon on 2008-09-12
> **dannyboy79 said:**
> you'll have to run fsck from a livecd that doesn't mount your / (root) partition. Otherwise, no matter what your / partition is always going to get mounted if you run ubuntu which is installed on your computer. You will not be able to unmount / because it's in use by the system.

Maybe someone else will come along and be able to figure out why fsck isn't running when it should be. Have you tried a search within the forum or goggle?
Another safe way to do is open terminal and do
```
sudo touch /forcefsck
```
and on the next reboot it will start the *fsck* checking like if it had reached 30 boots (which obviously does not work for you for some reason).

Thus, every time you want to do a *fsck*, give the above command and reboot.

Hope that helps you :)

P.S.: and yes indeed, the warning that *fcsk* is giving you is valid. Never do a *fsck* checking on a mounted partition. Only the above command is safe.

---

