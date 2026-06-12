---
title: "Hard Drive Space Vanished"
date: 2008-07-01
forum: Hardware
---

### Post by mattydubs on 2008-07-01
(New to the forum) I installed Heron a month or so ago and now it's telling me I'm out of disk space.

This is on a single boot machine, with a brand new 320 Gigabyte Western Digital drive.  Now it is telling me I only have 5.1 gigs total and it is all used up (actually disk anaylzer tells me I have 10...)

Any ideas or do I have to format and re-install?  (Which would, of course, suck a bit at this point).

Thanks!

PS, here is the output of DF

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              5642032   5517412         0 100% /
varrun                 1031096        96   1031000   1% /var/run
varlock                1031096         0   1031096   0% /var/lock
udev                   1031096        56   1031040   1% /dev
devshm                 1031096        12   1031084   1% /dev/shm
lrm                    1031096     43040    988056   5% /lib/modules/2.6.24-19-generic/volatile
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon       5642032   5517412         0 100% /home/ezweave/.gvfs
/dev/scd0                 9028      9028         0 100% /media/cdrom0

---

### Post by ibutho on 2008-07-01
Thats weird. What is the output of running a terminal and entering
```
sudo fdisk -l
```

---

### Post by kevmitch on 2008-07-01
Yeah, your system should take any more than 20G, and that's being really liberal about it. It looks like you don't have a separate home partition. Try

```
du /home | sort -g
```

That will give you a ascending list of files and directories by size. If /home can't account for 30-40Gb, then try 

```
du / | sort -g
```

---

