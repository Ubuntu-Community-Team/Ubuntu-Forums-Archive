---
title: "[SOLVED] Unable to mount WD Caviar Green 1TB as a secondary SATA drive"
date: 2008-11-29
forum: Hardware
---

### Post by mistergoomba on 2008-11-29
Sorry to repost, but I realized that the original summary did not help people understand my problem.

I just installed a SATA WD Caviar Green 1TB drive. My primary drive is also SATA. When I booted to my old drive and tried to open my new drive, it was labeled SCSI Drive and said "Could not mount drive". There didn't seem to be any other details.

If anyone has any suggestions, I'd love some help. Searching the forum it seems that others have been able to use this drive no problem. Do I have to format it? How would I do that?

Thanks in advance, and once again I apologize for the repost.

---

### Post by skozzy on 2008-11-30
Im new with the concept of setting up drives in linux, but I believe before you can use it you have to use the partiton editor to write a disk label to the drive and make a partition.

---

### Post by mistergoomba on 2008-11-30
Ok, so I used GParted to partition the disk into an ext3 filesystem. I then restarted because there was no icon for the drive at all anymore.

When I restarted, I got this window: "There was an error starting the GNOME Settings Daemon. Some things, usch as themes, sounds, or background settings may not work correctly. The Settings Daemon restarted too many times. GNOME will still try to restart the Settings Daemon next time you log in."

I was able to find my labeled drive and attempted to open it. I got a dialog box asking me to authenticate. I put in my password, pressed "authenticate", but nothing happened. The drive will not mount. I checked the device manager, and it is definitely recognized. I even tried reformatting to ext2 for the heck of it.

Any ideas?

---

### Post by taurus on 2008-11-30
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by mistergoomba on 2008-11-30
```

$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e8b3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38559   309725136   83  Linux
/dev/sda2           38560       38913     2843505    5  Extended
/dev/sda5           38560       38913     2843473+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008573

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

```

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4c1941f2-5b1d-4976-a13a-bbb0443cfe66 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3259038e-c433-44f3-a5cf-bdf569ca6c1c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```

~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             291G  275G  1.3G 100% /
varrun                474M  104K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   56K  474M   1% /dev
devshm                474M   12K  474M   1% /dev/shm
lrm                   474M   38M  437M   8% /lib/modules/2.6.24-12-generic/volatile
gvfs-fuse-daemon      291G  275G  1.3G 100% /home/martin/.gvfs

```

---

### Post by taurus on 2008-11-30
Try

```
sudo mkdir /media/sdb1
sudo mount -t ext2 /dev/sdb1 /media/sdb1
df -h
```

p.s.  By the way, you know that you've maxed out 291GB of your /?

---

### Post by mistergoomba on 2008-11-30
That's why I got the new hard drive ;}

Thanks a lot! I'm able to access my drive now.

---

