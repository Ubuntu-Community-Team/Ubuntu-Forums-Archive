---
title: "USB harddrive mount at startup / boot"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by GeeRoc on 2006-03-13
hi there!

one simple question i just cannot find an answer to:
**how can i make my already plugged in USB harddrive mount at boot?**

the drive is already plugged in when i power up (and it stays plugged in almost all the time). it's ubuntu 5.04 with gnome. when i start the machine bootup ends with the gnome login screen for the user. when i login the drive is mounted, but i need it to mount automatically, since this machine is used as a server.

when i do this manually by executing (in putty) the mount command like this:

```
sudo mount -t vfat -o rw,nosuid,nodev,quiet,uid=1001,gid=100,umask=077,iocharset=utf8 /dev/sda1 /media/extusb1
```

then the drive is available as i need it (as a samba share that is - therefore the uid=1001,gid=100 in etc. the mount command)

so again: how can i make the machine to automatically detect and mount my USB harddrive as i need it on bootup with the USb drive already plugged in?

thanks all!

---

### Post by Heliix on 2006-03-13
hi,
as root, add the following line to your /etc/fstab file

/dev/sda1  /media/extusb1  vfat  rw,nosuid,nodev,quiet,uid=1001,gid=100,umask=077,iocharset=utf8   0   0

it should work ;-)
Heliix

---

### Post by GeeRoc on 2006-03-13
[QUOTE=Heliix]hi,
as root, add the following line to your /etc/fstab file

/dev/sda1  /media/extusb1  vfat  rw,nosuid,nodev,quiet,uid=1001,gid=100,umask=077,iocharset=utf8   0   0

it should work ;-)
Heliix[/QUOTE]

sorry i didn't mention it, but i already tried that - didn't work. i geht this error:
```
mount: /dev/sda1 is not a valid block device
```

i think the hotplug system is still busy or not started at all when fstab is processed :(

any other suggestions?

---

### Post by GeeRoc on 2006-03-13
[QUOTE=GeeRoc]i think the hotplug system is still busy or not started at all when fstab is processed :([/QUOTE]
having said that, i changed the order of the rcS.d scripts by renaming "S40hotplug" to "S32hotplug" in /etc/rcS.d/ 
now the hotplug script is executed directly before "S35mountall.sh" and **everything works now**. \\:D/ 

another thing: to get chmod 777-like file permissions on the mounted drive i had to use umask=000 in the mount command, not umask=077 as mentioned above.

thanks to Heliix for the hintand good nite!

---

