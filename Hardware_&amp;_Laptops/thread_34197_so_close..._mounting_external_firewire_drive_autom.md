---
title: "so close... mounting external firewire drive automatically"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by jce on 2005-05-13
ok, so I've sucessfully partitioned/formatted my 250Gb maxtor external firewire drive;

i've sucessfully mounted the partition to a mount point i specified

sudo mount -t vfat  /dev/sda /home/mp3/share -o umask=0

then, i added this line to the end of my /etc/fstab

/dev/sda  /home/mp3/share vfat auto,umask=0,rw 0 0

HOWEVER..............

when i reboot, I get this message during the boot process:
mount: /dev/sda does not exist

but once the system finishes booting, I log in and fire up an xterm window and manually mount the partition, it works fine

what am i doing wrong ????? i need this to mount automatically.

---

### Post by Predius on 2005-05-14
[QUOTE=][/QUOTE]
 It needs to have sd_mod activated, which you may not have, perhaps the mounting is done before the modprobe is run.

You could add a script to init.d, if I am not mistaken, telling the machine to mount the drive.

---

### Post by jce on 2005-05-17
yup... that did it.

thanks for the help

---

