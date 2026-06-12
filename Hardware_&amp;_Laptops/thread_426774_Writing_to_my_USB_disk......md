---
title: "Writing to my USB disk....."
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by forsaken_pariah on 2007-04-28
I have a 20G USB hard drive and when I plug it in it automounts but I can't write to it without superuser privileges. I was wondering if there were any way to change the permissions so I can write to it without doing this. It's not really that big of a problem, but I keep my torrents on this drive and I have ktorrent set to run on startup w/ sudo and it's starting to get annoying to have to type in my password to start it every time I boot my computer, not to mention having to use sudo in a console every time I wanna write something else to it.

Any help would be greatly appreciated.


  Kory X.

---

### Post by taurus on 2007-04-28
Is it ntfs or vfat?  What's the output of these two commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by forsaken_pariah on 2007-04-29
It's ext3.

```

kory@hellbox:~$ sudo fdisk -l
Password:

Disk /dev/hda: 8455 MB, 8455200768 bytes
16 heads, 63 sectors/track, 16383 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16382     8256496+   7  HPFS/NTFS

Disk /dev/hdb: 13.5 GB, 13578485760 bytes
255 heads, 63 sectors/track, 1650 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1579    12683286   83  Linux
/dev/hdb2            1580        1650      570307+   5  Extended
/dev/hdb5            1580        1650      570276   82  Linux swap / Solaris

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
kory@hellbox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              12G  9.5G  1.9G  84% /
varrun                252M   96K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  136K  252M   1% /proc/bus/usb
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
/dev/hdc              588M  588M     0 100% /media/cdrom0
/dev/sda1              11G  2.0G  8.5G  19% /media/disk

```

---

### Post by taurus on 2007-04-29
Looks like /dev/sda1 is the one you want to have write permission to without using sudo or gksudo.  From a terminal, run

```
sudo chown -R **kory**:**kory** /media/disk
ls -la /media
```

---

### Post by forsaken_pariah on 2007-04-29
Gosh. That worked. I swear I've tried chown and chmod and all that stuff on /media/disk before and it didn't do anything.  But I'm just glad it works now.

Thanks a bunch!!!

Kory X.

---

