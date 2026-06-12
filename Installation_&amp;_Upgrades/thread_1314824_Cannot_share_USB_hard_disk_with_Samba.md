---
title: "Cannot share USB hard disk with Samba"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by QvasiModo on 2009-11-04
After upgrading to Karmic I can't find a way to share folders for guest access with Samba when they are located in a USB device (in my particular case, a removable hard drive). Other folders seem to be shareable to guests.

I'm using Ubuntu 9.10 64 bits, and I'm trying to share folders from the Nautilus GUI.

Here's what I see in the logs:
```

root@hostname:/var/log/samba# cat log.client 
[2009/11/04 20:36:51,  0] smbd/service.c:1009(make_connection_snum)
  '/media/usbharddrive/Shared' does not exist or permission denied when connecting to [shared] Error was Permission denied

```

The directory '/media/usbharddrive/Shared' exists and my user has permissions to access it (I can browse files locally with Nautilus).

```

root@hostname:/media# ls -l
total 20
lrwxrwxrwx 1 root   root       6 2009-09-14 18:46 cdrom -> cdrom0
drwxr-xr-x 2 root   root    4096 2009-09-14 18:46 cdrom0
drwx------ 1 user   user   16384 2009-11-03 20:43 usbharddrive

```

Where "user" is my user name, "hostname" is my host name, and "client" is another machine.

Please let me know what other information you need me to post here. I'm an Ubuntu newbie so be patient if I'm missing something obvious! ;)

---

### Post by SteveDee on 2009-11-09
I managed to share my USB memory device on 9.04 easily using one method, but this didn't work on 9.10.

So using the info here: [http://opensuse.swerdna.org/susefat32.html](http://opensuse.swerdna.org/susefat32.html)
I created a share as follows:-
- identify your USB drive (e.g. /dev/sdb1). You can do this via System > Administration > Disk Utility.
- Open Nautilus with root access via terminal command:-
gksu nautilus
- Create a mount point for your file system (e.g. /media/usbstick).

Modify /etc/fstab as follows:-
- from another terminal:-
gksu gedit /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dc7c3e4c-73c1-4bd9-96ae-aca1405bd761 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c0076633-e617-40b7-b233-dd9cb14590b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
[COLOR="Green"]#Add my memory stick
/dev/sdb1 /media/usbstick vfat uid=root,gid=users,umask=0000,utf8=true 0 0[/COLOR]

```
[COLOR="Red"]Note: last line in this file must be blank.[/COLOR]

- In terminal do:-
sudo mount -a

You should already be able to see the usbstick as a local drive

- Open Nautilus as root from terminal:-
gksu nautilus
- Navigate to /media/usbstick
- Right click and select Properties > Share
- Enable "Share this folder" and "Guest access".
- Change default share name if required, and then Create Share.

You should now be able to access your USB device over network.

---

### Post by diamant_g1 on 2009-11-29
Thank you! It's working for me too.

---

