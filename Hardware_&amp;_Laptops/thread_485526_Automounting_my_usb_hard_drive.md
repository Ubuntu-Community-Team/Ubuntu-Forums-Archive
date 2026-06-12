---
title: "Automounting my usb hard drive"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by elsaturnino on 2007-06-27
So, this is something that has been bothering me recently. I recently managed to get my wife to switch to using ubuntu. Everything has been going pretty well except for my darned Seagate USB hard drive. She has files on there that she wants to use but it doesn't automount when you turn it on. My /etc/fstab looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=b4c2e8d1-7c47-46c1-956e-14c8a1000b84 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8e90913b-1324-474f-88d6-dcf6d53965d5 /boot           ext3    defaults        0       2
# /dev/sda8
UUID=68380bc5-7cf6-49bc-ba13-5c98ac4abb69 /home           ext3    defaults        0       2
# /dev/sda6
UUID=c56b8994-0307-428f-aedc-b7b8e9d4221d /tmp            ext3    defaults        0       2
# /dev/sda5
UUID=797e28b5-aee4-4649-ad49-c2ae512feaf0 none            swap    sw              0       0
# /dev/sdb1
/dev/sdb1 /media/SeagateHD      vfat    users,noauto,gid=100,umask=007  0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# brother mfc-240c stuff
none /proc/bus/usb usbfs auto,devmode=0666 0 0

```

Mounting the old fashioned way (mount /media/SeagateHD) works but my wife doesn't want to have to deal with doing that. Any ideas why this thing won't automount? I've poured over the forum with people having similar problems but none of them seem to be resolved. Is this just a problem with Feisty/Ubuntu?

---

### Post by merlinus on 2007-06-27
> 
/dev/sdb1 /media/SeagateHD vfat users,noauto,gid=100,umask=007 0       0

You might try changing noauto to auto.

Also, look in System/Preferences/Removable Drives and Media to 
ensure the correct boxes are ticked.

merlin

---

### Post by elsaturnino on 2007-06-27
Switching from noauto to auto made it mount on bootup but it won't automount otherwise. The appropriate boxes are checked in the removable drives and media preferences too. My USB key drives will automount but not the hard drive.

---

### Post by elsaturnino on 2007-06-27
shameless bizzump

---

### Post by ugm6hr on 2007-06-27
I'm no expert, but my 2.5" USB HD automounts when plugged in on Xubuntu7.04

My suggestion - just delete the entry in /etc/fstab corresponding to sdb1.

If you want it to mount in /media/SeagateHD, just rename the partition SeagateHD.

Mine is called WDPassport (it's a Western Digital Passport), which I named in XP, and it auto-mounts to /media/WDPassport.  

However, it doesn't automount if plugged in at startup.  But it can be mounted from the desktop (on Xubuntu) or Thunar file manager (as I'm sure Nautilus will).

---

### Post by elsaturnino on 2007-06-27
Well, I have the drive labeled as SeagateHD but even before I added the fstab entry, it didn't automount. What file system type do you have on your external hd?

---

### Post by moore.bryan on 2007-06-27
[I]you could always try the following setup:
```
/dev/sdb1     /media/SeagateHD     auto     defaults     0     0

```
[/I]

---

### Post by elsaturnino on 2007-06-27
> **moore.bryan said:**
> [I]you could always try the following setup:
```
/dev/sdb1     /media/SeagateHD     auto     defaults     0     0

```
[/I]

no dice...

---

### Post by moore.bryan on 2007-06-27
[I]even after a restart?  hmm... i wonder if mount and pmount are both trying to handle the drive.  i'm guessing that because you've put it in fstab it is always attached to your computer; correct?
do you have a directory in /media called "SeagateHD?"
[/I]

---

### Post by elsaturnino on 2007-06-27
> **moore.bryan said:**
> even after a restart?  hmm... i wonder if mount and pmount are both trying to handle the drive.  i'm guessing that because you've put it in fstab it is always attached to your computer; correct?
do you have a directory in /media called "SeagateHD?"
[/I]

Well, until this morning, I didn't have pmount installed so I don't think that is/was the problem. I put it in the fstab because I heard some rumors that you need to do this to make it automount. Obviously it didn't exactly help but at least it made mounting it a bit quicker (mount /media/SeagateHD). And, yes, /media/SeagateHD exists.

---

### Post by moore.bryan on 2007-06-27
[I]so, when you start your computer, you need to manually type "sudo mount -a?"  i agree, that's a pain.  are you sure the external hard drive is /dev/sdb1?
what's the output of ```
sudo fdisk -l
```[/I]

---

### Post by elsaturnino on 2007-06-27
I just type mount /media/SeagateHD whenever i want to mount it. It mounts fine (yes, the sdb1 thing is correct) it just doesn't automount when i turn on the hard drive.

---

### Post by ugm6hr on 2007-06-28
> **elsaturnino said:**
> Well, I have the drive labeled as SeagateHD but even before I added the fstab entry, it didn't automount. What file system type do you have on your external hd?
My WDPassport is fat32 - which looks the same as yours.  

Given USB flash disks auto-mount (which are mainly fat16/fat32), it seems bizarre that the Seagate doesn't.  Maybe there is a technical difference between turning a USB drive in (that's already plugged in) and plugging it in?  I don't know - mine takes power from the USB port, so there's no on/off switch.  Or maybe Thunar and Nautilus auto-mount differently (I use Xubuntu)?

A possible temporary solution is to add a panel shortcut with the mount command, to mount the HD with a single click.

---

### Post by elsaturnino on 2007-12-18
Well, several months later and the problem is finally "fixed."  Turns out that Seagate's initial formatting of the drive leads to some parameters that udev doesn't like so it doesn't automount it.  The solution was just to reformat the drive (again, as fat32 so it can speak to windows (boooo!) if need be). Voila! All good.  Here is the link that helped me finally close the case (in case you are having similar problems).

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/147807](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/147807)

---

