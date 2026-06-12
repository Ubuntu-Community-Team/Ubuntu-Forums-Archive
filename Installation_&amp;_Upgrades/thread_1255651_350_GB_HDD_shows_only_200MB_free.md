---
title: "350 GB HDD shows only 200MB free"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by iboot on 2009-09-01
Just installed 9.04 on an HP tx2z tablet PC. I selected the "Use entire disk" option to install ubuntu (without any further partitioning) on the drive.

After boot, I see only the file system in places..computer and there is less than 300MB of free space. I don't have anything on the drive except the ubuntu since I wiped out the OEMs Vista OS and recovery partitions. There should be 300GB+ of free space.

Any ideas what happened? I also tested the install by installing as a dual boot with XP on an 80GB drive with similar result. It seems that the partition ubuntu created for itself was too small so it could not install upgrades (I got the insufficient disk space error) even though it could "see" the XP partition in this case.

Thanks,

iboot.

---

### Post by falconindy on 2009-09-01
Ubuntu creates a /swap partition on installation. I suspect this is where your "missing" disk space is. Pop open a terminal and do:
```
cat /proc/swaps
```

---

### Post by iboot on 2009-09-01
ok, so looks like there is some space here. How do I reclaim it? I originally tried a dual boot on this machine but now am running only ubuntu. 

Filename                Type        Size    Used    Priority
/dev/sda5                               partition    8305564    0    -1

---

### Post by falconindy on 2009-09-01
> **iboot said:**
> ok, so looks like there is some space here. How do I reclaim it? I originally tried a dual boot on this machine but now am running only ubuntu. 

Filename                Type        Size    Used    Priority
/dev/sda5                               partition    8305564    0    -1
Well, you're only looking at 8gb claimed there. Nothing too serious. What about the results of doing `df -h`? Since you're only running a single hard drives, the results of the df command *should* add up to something more reminiscent of the total drive size (minus the 8gb from the /swap and some overhead).

Also, keep in mind that when a manufacturer claims a drive to be 350GB, you don't really get that much space. It's an advertising gimmick where they measure the size in GB (gigabytes), but you really only get that much space in GiB (gibibytes). Wikipedia has a fairly decent table showing the difference:

[http://en.wikipedia.org/wiki/Orders_of_magnitude_(data](http://en.wikipedia.org/wiki/Orders_of_magnitude_(data))

---

### Post by iboot on 2009-09-02
Thanks. It seems I see it now.

boot@HPTX2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             286G  2.7G  269G   1% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  124K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  168K  1.4G   1% /dev
tmpfs                 1.4G   88K  1.4G   1% /dev/shm
lrm                   1.4G  2.2M  1.4G   1% /lib/modules/2.6.28-15-generic/volatile

---

