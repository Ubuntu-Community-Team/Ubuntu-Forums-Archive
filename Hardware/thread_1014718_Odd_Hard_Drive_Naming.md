---
title: "Odd Hard Drive Naming"
date: 2008-12-18
forum: Hardware
---

### Post by nathano on 2008-12-18
Hello,

While trying to setup a RAID1 array, I've run into a little issue; my /etc/fstab indicates that /dev/sda1 is mounted as / but other sources (for example, df) indicate that /dev/sdb1 is the real /:

fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=214b9c03-8a1c-4a9b-ac55-16bf8a98239b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ea59c508-67a4-4f43-b84a-beb7ab2706bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

df -h:```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             227G  7.5G  208G   4% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  336K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  152K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-9-generic/volatile
```

/proc/partitions indicates I have three disks; two 80 GB drives and a 250 GB drive. I know that the 250 is / and /proc/partitions claims this to be /dev/sdb:

/proc/partitions:```
major minor  #blocks  name

   8     0   78150744 sda
   8     1   78148161 sda1
   8    16  244198584 sdb
   8    17  241199878 sdb1
   8    18          1 sdb2
   8    21    2996091 sdb5
   8    32   78150744 sdc
   8    33   78148161 sdc1
```

I would like to create a RAID1 of the two 80 GB drives... but I need to make sure fstab is a part of the plan :-) Here's my mdadm output:

```
sudo mdadm --create /dev/md0 --chunk=64 --level=1 --raid-devices=2 /dev/sda1 /dev/sdc1
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: create aborted
```

Anyone know why fstab (and apparently mdadm) would be the only thing thinking my 250 GB drive is /dev/sda?

---

