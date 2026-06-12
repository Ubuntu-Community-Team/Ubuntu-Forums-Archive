---
title: "USB HDD Won't mount at startup"
date: 2009-10-03
forum: Hardware
---

### Post by bircoe on 2009-10-03
I'm having problems getting a Western Digital 1tb My Book (formatted as fat32) to mount at start up, I've tried a ton of different fstab mount options but nothing seems to work, after mythbuntu is fully loaded I can issue a 'sudo mount -a' or 'sudo mount /media/TV' and the drive will mount without complaint, and to get around this I've put the 2nd command in my rc.local file to get the drive to mount.

The problem here is I use mediatomb to share media around the house but mediatomb starts before the rc.local script is run, which causes a couple of problems, restarting mediatomb is usually not enough to get it to notice the content on /media/TV I also have to recreate it's database, which is an annoying manual task.

I've tried putting '/etc/init.d/mediatomb start' (after disabling auto start) in the rc.local file but this doesn't seem to work...

Is there something wrong with my fstab file causing the drive to not mount?
For the record /media/Movies mounts automaticly before mediatomb starts.
 
fstab:
```

UUID=9d14d6d1-ac89-46fa-8f7c-bd5c4674e327  /media/Movies  ext3         rw,user,exec                1  2
UUID=5A23-9D9B                             /media/TV      vfat         rw,auto,user,umask=000      0  0

```sudo fisk -l
```

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    b  W95 FAT32

```ls /dev/disk/by-uuid/
```

total 0
lrwxrwxrwx 1 root root 10 2009-10-04 12:49 1f17a2df-e703-458c-98be-ba510447d135 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-10-04 12:49 2c93afad-4f0b-45d3-b292-ffae8f0035e7 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-10-04 12:49 5A23-9D9B -> ../../sdc1
lrwxrwxrwx 1 root root 10 2009-10-04 12:49 9d14d6d1-ac89-46fa-8f7c-bd5c4674e327 -> ../../sdb1

```

---

### Post by bircoe on 2009-10-05
So I've managed to get everything happy after boot by making a script that does the following:
Stop Media Tomb
Mount the TV Disk
Mount the Movies Disk <= this one mounts fine but I figured I'd add it anyway.
Start Media Tomb

I'm calling this script from the rc.local file and I have a fully populated media database afterwoods, I don't consider this a fix for my problem I consider it a hack to make it work.

rc.local
```

/home/myth/startmediatomb | tee /home/myth/mediatomb.log
exit 0

```startmediatomb.sh
```

#!/bin/sh
start (){
SERVICE=$1
$SERVICE > /dev/nul
APTEXIT=$?

if [ $APTEXIT = 0 ]; then
    echo $(date) - \"$SERVICE\" completed successfuly
else
    echo $(date) - \"$SERVICE\" failed
fi

}

start '/etc/init.d/mediatomb stop'
start 'mount /media/TV'
start 'mount /media/Movies'
start '/etc/init.d/mediatomb start'

```mediatomb.log
```

Sun Oct 4 18:13:05 EST 2009 - "/etc/init.d/mediatomb stop" completed successfuly
Sun Oct 4 18:13:05 EST 2009 - "mount /media/TV" completed successfuly
Sun Oct 4 18:13:05 EST 2009 - "mount /media/Movies" failed
Sun Oct 4 18:13:05 EST 2009 - "/etc/init.d/mediatomb start" completed successfuly

```

---

