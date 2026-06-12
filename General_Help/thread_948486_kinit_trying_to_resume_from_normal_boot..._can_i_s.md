---
title: "kinit trying to resume from normal boot... can i stop this?"
date: 2008-10-15
forum: General Help
---

### Post by shawnrgr on 2008-10-15
I've install normal ubuntu-desktop before on my compaq laptop and never received these messages at boot. However I've recently installed ubuntu-base only from a minimal cd. When the system starts to boot up the first thing I get is the following:
```
kinit: name_to_dev_t(/dev/disk/by-uuid/65917b90-bf26-45ab-9244-967b7d8eb1f0) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/65917b90-bf26-45ab-9244-967b7d8eb1f0
kinit: No resume image, doing normal boot...
resume: libgcrypt version: 1.2.4
...
```
Is the system trying to resume from like a hibernated or suspended state? I'm running OpenBox and shutdown from my menu that runs "gksudo /sbin/shudown -h now" so I'm def not putting the system in a suspended state.

It wouldn't be an issue for me if I wasn't trying to speed up my boot time. This process adds about 3-5 seconds to my total boot time. I would really like to stop it from doing this.

Below is my fstab in case its somehow related:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8ae98ac2-79fb-42b3-a1d4-926597ce646e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=65917b90-bf26-45ab-9244-967b7d8eb1f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Shared folder from Freedom
boxee:/media/storage /media/boxee/storage nfs rsize=8192,wsize=8192,timeo=14,intr
#Shared folder from Freedom
boxee:/media/storage2 /media/boxee/storage2 nfs rsize=8192,wsize=8192,timeo=14,intr
```

---

### Post by shawnrgr on 2008-10-15
Sorry for the bump, anyone? I've looked around and found some unresolved old posts but thats really it.

---

### Post by shawnrgr on 2008-10-16
*bump*  :(

---

### Post by mkrahmeh on 2008-10-16
sorry if this is not informative as you hope, but i think kinit looks for an image taken for the RAM and saved on the HDD..that is for hibernating, if the image is not found, then normal boot is carried on.

as far as i can imagine, there might a start up script that invokes the kinit every time your system starts up (most likely the ones in /boot/), so try to locate start up scripts, then search for the word kinit in them, you may find something..

i dont want to recommend commenting lines that start the kinit, we dont want compromise your system's boot :)

---

### Post by buggycode on 2008-10-23
This is happening on my machine with a fresh amd64 install of 8.04
Hold the boot sequence up for about 20 seconds especially if there is a no bootable cd/dvd in the drive.

What confuses me is that the dvd drove is not first on bootable device list in the BIOS.

This only started to happen recently.
On advive I ran sudo update_initramfs -u.  Made things worse - now the dvd/cd rom does not work.

I upgraded the system and no the Video Card, Network connection and Virtualbox no longer work.

I don;t know if any of this is related - however the problem and now more still remain.

---

### Post by gairaldi on 2008-11-23
i have the same problem with my compaq f700 series notebook, but if you press the ALT key, the boot starts faster

---

