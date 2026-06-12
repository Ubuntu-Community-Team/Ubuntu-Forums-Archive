---
title: "Backup Permission denied?"
date: 2012-11-16
forum: Hardware
---

### Post by RezPix on 2012-11-16
Hi guys, I formatted a 500GB drive thats installed on my desktop. I run my main OS from a 60GB SSD and have a 750GB & 3TB drives for Media etc... However when I try to use the backup feature and tell it to backup on my "Backup Drive" (500GB) it says "Permission denied". Does anyone have any ideas why this may be happening?

Many thanks,
Josh

---

### Post by jerome1232 on 2012-11-16
Probably you just need to take ownership of it, how did you mount this, via gui or manually?

Should be somethign like

```
sudo chown $USER:$USER [COLOR="Red"]/path/to/backup/drive[/COLOR]
```

---

### Post by RezPix on 2012-11-16
thanks for the fast reply! I just put it in, used GPARTED to format and mount it, it showed up in my home folder, just take do anything with it... :L ill try that command you just said about..

---

### Post by RezPix on 2012-11-16
What would be the path to my backup drive?

---

### Post by jerome1232 on 2012-11-16
What's the output of this command

```
mount
```

---

### Post by RezPix on 2012-11-16
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdd2 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/josh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=josh)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/Backup type ext4 (rw)

So im assuming /media/Backup would be the Backup drive?

---

### Post by jerome1232 on 2012-11-16
Yup, although I would think the gui should've taken care of permissions for you, go ahead and chown it.

---

### Post by RezPix on 2012-11-16
Ahh Brilliant! I got it working! Thank you! The only issue is that when I try to use GPARTED to mount my 3TB Drive, I get an error. [http://postimage.org/image/6t4ban7th/](http://postimage.org/image/6t4ban7th/)

Any help would be great!

---

### Post by jerome1232 on 2012-11-16
With disks that big you should use gpt partitioning instead of ms-dos partitioning.

That's what I use on my 3 TB disk.

---

### Post by RezPix on 2012-11-16
Thanks, but how do I setup GPT partitioning? I was a bit shocked when i saw MSDOS dunno why that was coming up?

---

### Post by jerome1232 on 2012-11-16
It's just a partition table, everyone pretty much uses MSDOS partition tables, and everyone is transitioning into GPT soon as we've hit the upper limits of MSDOS partition tables.

GPT has many advantages however Windows can't boot from it unless you have a newer UEFI setup instead of the old BIOS setup, this is all moot since your just using it for a backup disk :D

Anyways, changing the partition table will destroy all partitions and data on the disc, so take any files off. Select the disk in gparted just like in your screenshot, make sure it's unmounted, then click devices and create partition table, select GPT from the drop-down menu. Then feel free to create partitions and format them to the desired file system.

---

### Post by RezPix on 2012-11-17
I do appoligise for the reply. I has been a while and didn't realize that there was a page 2. This worked for me. Thank you very much! Why would you want to use GPT or MSDOS? And why would you use MSDOS tables in linux? thanks!

---

