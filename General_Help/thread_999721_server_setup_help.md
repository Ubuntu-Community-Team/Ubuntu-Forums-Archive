---
title: "server setup help"
date: 2008-12-02
forum: General Help
---

### Post by qaazaa on 2008-12-02
hi there my fellow ubuntu users well i have seem to have done something with my server this is a problem thats lost me seems one of my mounts needs remounted

heres the error is there a way to fix this thanks

# <sys.fichiers><pt de montage><type> <options>  <dump> <pass>
/dev/sda1	/	ext3	errors=remount-ro,relatime	0	1
/dev/sda2	swap	swap	defaults	0	0
/dev/sda3	/home	reiserfs	defaults	1	2
proc            /proc   proc    defaults        0       0
sysfs           /sys    sysfs   defaults        0       0

and server is using ..

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

---

### Post by taurus on 2008-12-02
I am not sure if I understand what you mean by one of your mounts needed remount?  Can you post the outputs of these commands?

```
sudo fdisk -l
df -h
free
```
Your swap partition, /dev/sda2, looks a little odd.  It should look something like this.

```
/dev/sda2   none   swap   sw   0   0
```

---

### Post by qaazaa on 2008-12-02
i did your steps heres the results

root@ns:~# sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750155325440 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bd371

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276        1912     5116702+  82  Linux swap / Solaris
/dev/sda3            1913       91201   717213892+  83  Linux

--------------------------------------------------------------------------------------------------------------------

root@ns204913:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
rootfs                9.7G  4.2G  5.0G  46% /
/dev/root             9.7G  4.2G  5.0G  46% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  228K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
/dev/root             9.7G  4.2G  5.0G  46% /dev/.static/dev
udev                  2.0G  2.7M  2.0G   1% /dev
tmpfs                 2.0G   24K  2.0G   1% /dev/shm
/dev/sda3             684G  321G  364G  47% /home

---------------------------------------------------------------------------------------

root@ns:~# free
             total       used       free     shared    buffers     cached
Mem:       4137340    4018284     119056          0      49100    3385984
-/+ buffers/cache:     583200    3554140
Swap:      5116692       2864    5113828
root@ns:~#

---

### Post by taurus on 2008-12-02
I don't see anything wrong with your system now since you have / for 9.7GB while /home takes up 684GB with about 5GB of swap.

---

