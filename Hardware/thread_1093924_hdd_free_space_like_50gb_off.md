---
title: "hdd free space like 50gb off :/"
date: 2009-03-12
forum: Hardware
---

### Post by dexmans on 2009-03-12
Hey people,

My first post on the ubuntu forum.
I've been using ubuntu desktop/server for a couple of years now, no hardcore stuff but just running a webserver/ftp and playing around.

So far so good and I've never had complaints or things i couldn't solve by just googling or looking at these forums.

But now I have an issue that I can't fix by searching so I'll need the help of the ubuntu people :)

My problem:
When I check my used diskspace with df -h 1 of my disks 87% in use.
But it's not.

I've installed Ubuntu 8.10 server a while ago and I have /home/ on a separate mount. (More diskspace available and easy for backups etc)

Output from # df -h
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   58G  9.0G  87% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  860K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  2.7M  1.6G   1% /dev
tmpfs                 1.6G     0  1.6G   0% /dev/shm
/dev/sdd1             917G  284G  588G  33% /mnt/ftp1
/dev/sdc1             917G   18G  853G   2% /mnt/ftp2
/dev/sdb1             151G  1.1G  143G   1% /home


It's about /dev/sda1 which only has like 6 or 7gb of data on it according to # du -hsc /*
> 5.4M    /bin
13M     /boot
0       /cdrom
2.7M    /dev
5.1M    /etc
866M    /home
0       /initrd.img
125M    /lib
0       /lib64
16K     /lost+found
8.0K    /media
301G    /mnt
4.0K    /opt
du: cannot access `/proc/31528/task/31528/fd/3': No such file or directory
du: cannot access `/proc/31528/task/31528/fdinfo/3': No such file or directory
du: cannot access `/proc/31528/fd/3': No such file or directory
du: cannot access `/proc/31528/fdinfo/3': No such file or directory
0       /proc
44K     /root
7.3M    /sbin
4.0K    /srv
0       /sys
16K     /tmp
511M    /usr
5.4G    /var
0       /vmlinuz
307G    total

301gb is used by mnt, which is correct according to the df output and what it should be imo.

But what happened to the other 52gb on /dev/sda1?

Does anyone have a clue? If you need more info let me know.

---

### Post by dexmans on 2009-03-12
bump

Is it possible that the hdd is just failing?
After all, it's a pretty old 80gb hdd

---

### Post by dexmans on 2009-03-12
pff..

Never mind found the problem...
While reinstalling my pc I copied some data (50gb ;) ) to a dir I thought was mounted..
But it wasn't and when I mounted the disk on that dir the data of course was missing.

Unmount, copy to new location remount and it's all working again :P

---

