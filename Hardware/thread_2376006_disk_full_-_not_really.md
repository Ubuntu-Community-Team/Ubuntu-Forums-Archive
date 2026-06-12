---
title: "disk full - not really"
date: 2017-10-29
forum: Hardware
---

### Post by jgw on 2017-10-29
This morning I get an advise that my home drive was full and to delete the trash.  I did that.  I still had the error.  This made no sense so I re-booted and then it turns out that it was not full (500gb drive, 25gb used, the rest free).  Then it happened again.  I checked the trash and it was full of stuff.  I deleted it again and rebooted and am currently fine.  I have absolutely no idea what happened.  I also went to 'disks' and checked the drive and everything was dandy.  I did noticed the when I checked the drive, and it finished reading the drive, that it had read 24gb but said 25gb were being used.  I suspect that is probably due to bad sectors.

Anyway, I was wondering if this has happened to anybody and, if so, did it get figured out?

Thank you...........

---

### Post by ian-weisser on 2017-10-29
Please open a terminal and show us the complete output of the following commands:
```
df
df -i
```

---

### Post by jgw on 2017-11-01
Thank you for the reply.  Since I submitted this I have rebooted 3 times and the problem seems to have gone away (its all done with smoke and mirrors).  I have also updated and upgraded (w/"sudo apt upgrade" and synaptic)

greg@movies:~$ df
Filesystem      1K-blocks       Used  Available Use% Mounted on
udev              4032472          0    4032472   0% /dev
tmpfs              811680      80964     730716  10% /run
/dev/sda1       472388888   25524748  422845096   6% /
tmpfs             4058392       4064    4054328   1% /dev/shm
tmpfs                5120          4       5116   1% /run/lock
tmpfs             4058392          0    4058392   0% /sys/fs/cgroup
/dev/sdb1      3845577736 1355106416 2295104104  38% /mnt/data
tmpfs              811680         84     811596   1% /run/user/1000
greg@movies:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             1008118    578   1007540    1% /dev
tmpfs            1014598    856   1013742    1% /run
/dev/sda1       30007296 615330  29391966    3% /
tmpfs            1014598     47   1014551    1% /dev/shm
tmpfs            1014598      5   1014593    1% /run/lock
tmpfs            1014598     16   1014582    1% /sys/fs/cgroup
/dev/sdb1      244195328  61898 244133430    1% /mnt/data
tmpfs            1014598     39   1014559    1% /run/user/1000

---

