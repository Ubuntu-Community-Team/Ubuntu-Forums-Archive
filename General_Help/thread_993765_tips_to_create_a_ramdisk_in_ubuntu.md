---
title: "tips to create a ramdisk in ubuntu"
date: 2008-11-26
forum: General Help
---

### Post by bhuvi on 2008-11-26
i have written a blog about creating a ramdisk in linux at [http://blulin.wordpress.com/2008/11/28/tips-to-create-ramdisk-in-a-linux-system/](http://blulin.wordpress.com/2008/11/28/tips-to-create-ramdisk-in-a-linux-system/) hope it will be useful for you

---

### Post by talsemgeest on 2008-11-28
Please mark this thread as solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Jouke74 on 2008-11-28
It's much safer to use the temporary file system instead of the limited ramdisks the kernel makes. 

- Make a mount point folder under /media e.g. "ramdisk"
- To increasae the size, change the 128 to whatever. Note don't increase this size too much, you need still some free memory.
- Warning, with a reboot all data from the Ramdisk will be deleted!

Then run the following script or commands, where the echo's are not essential:

[I]echo '**************************'
echo ' Creating 128 MB Ramdisk.'
echo '**************************'
sudo mount -t tmpfs tmpfs -o size=128M,nr_inodes=1M /media/ramdisk
sudo chown {yourusernamehere}:root /media/ramdisk
sudo chmod 0770 /media/ramdisk[/I]

---

### Post by bhuvi on 2008-11-29
what is the use of temporary file system?actually what is the difference between the two

---

### Post by Jouke74 on 2008-12-01
The temporary file system is basically the same as the ramdisk. It allows you to make a chuck of your ram available as disk. The advantage is that it can also be set dynamically. So the amount of memory used is 32 Mb the actual amount of memory used is also 32 Mb. This gives a bit more freedom. It's basically the "new ramdisk". The other main advantage is that you don't need to mess with your kernel parameters.

[http://en.wikipedia.org/wiki/TMPFS](http://en.wikipedia.org/wiki/TMPFS)

---

### Post by ubun_two on 2008-12-01
I thought Ubuntu makes ramdisk space available automatically at /dev/shm...?

---

### Post by HermanAB on 2008-12-01
Hmm, if you need a ramdisk for speed, simply store your schtuff in /tmp since that is already a ramdisk - thus saving yourself the hassle of creating a new one.

---

### Post by lavinog on 2008-12-01
is /tmp really a ramdisk?
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              8168188   4843988   2992300  62% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                  451720       260    451460   1% /var/run
varlock                 451720         0    451720   0% /var/lock
udev                    451720        84    451636   1% /dev
devshm                  451720        40    451680   1% /dev/shm
devpts                       0         0         0   -  /dev/pts
/dev/sda3               964532     36708    878828   5% /boot
/dev/sda7             48062440  24877512  20743452  55% /home
/dev/sda8             85139184  19679680  61999752  25% /storage
securityfs                   0         0         0   -  /sys/kernel/security
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc

```
I don't see /tmp in the list

---

### Post by Slim Odds on 2008-12-01
> **lavinog said:**
> is /tmp really a ramdisk?


No

---

### Post by lavinog on 2008-12-01
I think I just proved it to myself that it isn't

```

df -h ;dd if=/dev/urandom of=/tmp/testfile bs=1M count=100;df -h;rm testfile;df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             7.8G  4.7G  2.9G  62% /
varrun                442M  260K  441M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   84K  442M   1% /dev
devshm                442M   40K  442M   1% /dev/shm
/dev/sda3             942M   36M  859M   5% /boot
/dev/sda7              46G   24G   20G  55% /home
/dev/sda8              82G   19G   60G  25% /storage
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 31.8561 s, 3.3 MB/s
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             7.8G  4.8G  2.8G  64% /
varrun                442M  260K  441M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   84K  442M   1% /dev
devshm                442M   40K  442M   1% /dev/shm
/dev/sda3             942M   36M  859M   5% /boot
/dev/sda7              46G   24G   20G  55% /home
/dev/sda8              82G   19G   60G  25% /storage
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             7.8G  4.7G  2.9G  62% /
varrun                442M  260K  441M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   84K  442M   1% /dev
devshm                442M   40K  442M   1% /dev/shm
/dev/sda3             942M   36M  859M   5% /boot
/dev/sda7              46G   24G   20G  55% /home
/dev/sda8              82G   19G   60G  25% /storage

```

---

### Post by theozzlives on 2008-12-01
if /tmp were a ramdisk, there would be no need for a /tmp partition

---

### Post by lavinog on 2008-12-01
> **theozzlives said:**
> if /tmp were a ramdisk, there would be no need for a /tmp partition

I'm not sure if i understand your statement.
Are you saying that /tmp would not be needed if it was a ramdisk?

---

### Post by Slim Odds on 2008-12-01
I think that he's saying that in some installs people make /tmp a separate partition.

I do that on one of my machines.

---

