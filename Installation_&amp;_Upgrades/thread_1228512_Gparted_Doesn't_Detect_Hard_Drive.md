---
title: "Gparted Doesn't Detect Hard Drive"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by Suff on 2009-08-01
As in this thread [http://ubuntuforums.org/showthread.php?t=629566](http://ubuntuforums.org/showthread.php?t=629566)
Gparted doesn't detect the HD with the live disk or without.

The computer is about 5 years old and has a pirated version of xp on it which i want to get rid of. Any help would be great!

---

### Post by x33a on 2009-08-01
post the output of
```
sudo fdisk -l
df -h
```

---

### Post by doas777 on 2009-08-01
also, does the drive show in your BIOS? if not, check your cabling, connections, and any jumper settings. if the Bios can't see it, there is little hope that the OS can.

good luck

---

### Post by Suff on 2009-08-01
The xp os still boots fine, idk how i would check it in the bios


Terminal results:

Disk /dev/sda: 2021 MB, 2021654016 bytes
64 heads, 63 sectors/track, 979 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x03e703e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         969     1953439+   6  FAT16


Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 502M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 502M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M   84K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  132K  501M   1% /dev
tmpfs                 502M   76K  501M   1% /dev/shm
rootfs                502M   17M  485M   4% /
/dev/sr0              699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 502M   12K  502M   1% /tmp
/dev/sda1             1.9G  3.2M  1.9G   1% /media/CRUZER II

---

### Post by doas777 on 2009-08-01
if it boots, then the bios sees it. I'm not sure why fdisk doesn't. fat16?

---

### Post by Suff on 2009-08-01
Its probably NTFS, but i wouldn't know.
I will try formating it from safemode

---

### Post by dandnsmith on 2009-08-01
Neither FAT nor NTFS would explain why the HDD isn't seen at all - both will give valid responses to linux fdisk.

I'd be looking at the linux boot messages to see just what hardware is detected (look in /var/log) - the controller and disk ought to be giving some sort of response to the probes.

I do wonder if you might have an overlay which is displacing stuff on the HDD, and this is why you don't see it (I had one such once, but that disk has long ago been junked as too small capacity, and I never experimented with linux in the last 5 years on it)

---

### Post by Suff on 2009-08-01
I used Dban to get it to work, and again thanks for the help.
[http://www.dban.org/download](http://www.dban.org/download)

---

