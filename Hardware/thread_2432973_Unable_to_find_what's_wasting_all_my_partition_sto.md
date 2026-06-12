---
title: "Unable to find what's wasting all my partition storage"
date: 2019-12-11
forum: Hardware
---

### Post by hikariws on 2019-12-11
This is really odd. I discovered my root partition was full when I was trying to use TAB on terminal and was getting error which ended up bash unable to write on disk, because it was full.

I have one partition for /boot, one for swap, one for / and one for /home.

Confirming on GPated, / has 100GB size, and 5,79GB free after I deleted some stuff specially on /var/cache.

But QDirStat reports / with a size o 8,5GB. df repots:

```
/dev/sda3                 102686324    96615528     811600 100% /
```

ll:

```
$ ll
total 109
drwxr-xr-x  25 root   root    4096 nov 15 06:10 ./
drwxr-xr-x  25 root   root    4096 nov 15 06:10 ../
drwxr-xr-x   2 root   root    4096 nov  8 06:57 bin/
drwxr-xr-x   4 root   root    1024 nov 27 06:52 boot/
drwxr-xr-x   2 root   root    4096 jul 24 19:08 cdrom/
drwxr-xr-x  19 root   root    4400 nov  4 12:55 dev/
drwxr-xr-x 150 root   root   12288 dez 11 16:50 etc/
drwxr-xr-x   5 root   root    4096 jul 24 20:14 home/
lrwxrwxrwx   1 root   root      32 nov 15 06:10 initrd.img -> boot/initrd.img-5.0.0-36-generic
lrwxrwxrwx   1 root   root      32 nov 15 06:10 initrd.img.old -> boot/initrd.img-5.0.0-35-generic
drwxr-xr-x  23 root   root    4096 jul 24 21:38 lib/
drwxr-xr-x   2 root   root    4096 fev  9  2019 lib64/
drwx------   2 root   root   16384 jul 24 19:06 lost+found/
drwxr-xr-x   3 root   root    4096 jul 24 19:19 media/
drwxr-xr-x   2 root   root    4096 fev  9  2019 mnt/
drwxr-xr-x   3 root   root    4096 jul 24 21:38 opt/
dr-xr-xr-x 352 root   root       0 out 20 18:09 proc/
drwx------   4 root   root    4096 jul 24 19:45 root/
drwxr-xr-x  43 root   root    1480 dez 11 16:49 run/
drwxr-xr-x   2 root   root   12288 out 12 18:35 sbin/
drwxr-xr-x   8 hikari hikari  4096 out 18 13:28 share/
drwxr-xr-x  12 root   root    4096 jul 25 01:49 snap/
drwxr-xr-x   2 root   root    4096 fev  9  2019 srv/
dr-xr-xr-x  13 root   root       0 dez  8 17:06 sys/
drwxrwxrwt  20 root   root    4096 dez 11 16:55 tmp/
drwxr-xr-x  11 root   root    4096 ago  9 15:33 usr/
drwxr-xr-x  17 root   root    4096 set 19 17:16 var/
lrwxrwxrwx   1 root   root      29 nov 15 06:10 vmlinuz -> boot/vmlinuz-5.0.0-36-generic
lrwxrwxrwx   1 root   root      29 nov 15 06:10 vmlinuz.old -> boot/vmlinuz-5.0.0-35-generic

```

Is there any way of finding out what's wasting over 90GB?

---

### Post by #&amp;thj^% on 2019-12-11
Show this:
```
**df -Th**
Filesystem     Type      Size  Used Avail Use% Mounted on
dev            devtmpfs  5.7G     0  5.7G   0% /dev
run            tmpfs     5.7G  2.4M  5.7G   1% /run
/dev/sda4      ext4      222G   35G  176G  17% /
tmpfs          tmpfs     5.7G     0  5.7G   0% /dev/shm
tmpfs          tmpfs     5.7G     0  5.7G   0% /sys/fs/cgroup
tmpfs          tmpfs     5.7G   52K  5.7G   1% /tmp
/dev/sda2      vfat      511M  101M  411M  20% /boot
tmpfs          tmpfs     1.2G   60K  1.2G   1% /run/user/1000
/dev/sdb       fuseblk   1.9T  1.5T  343G  82% /run/media/me/My Passport 25E1
/dev/sdc1      fuseblk   3.7T  584G  3.1T  16% /run/media/me/My Passport


```

---

### Post by robbdt on 2019-12-11
Obviously you're logged in with perms to view everything? ie root?

---

### Post by hikariws on 2019-12-11
df only shows partitions and other devices, not what's wasting their storage :/

```
$ sudo df -Th
Filesystem              Type      Size  Used Avail Use% Mounted on
udev                    devtmpfs  3,9G     0  3,9G   0% /dev
tmpfs                   tmpfs     789M  1,9M  787M   1% /run
/dev/sda3               ext4       98G   93G  762M 100% /
tmpfs                   tmpfs     3,9G   81M  3,8G   3% /dev/shm
tmpfs                   tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs                   tmpfs     3,9G     0  3,9G   0% /sys/fs/cgroup
/dev/loop1              squashfs  1,0M  1,0M     0 100% /snap/gnome-logs/81
/dev/loop2              squashfs  1,0M  1,0M     0 100% /snap/gnome-logs/73
/dev/loop6              squashfs   45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop11             squashfs   43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/sda1               ext4      372M  165M  184M  48% /boot
/dev/sda4               ext4      720G   18G  664G   3% /home
tmpfs                   tmpfs     789M     0  789M   0% /run/user/999
/dev/loop18             squashfs  4,3M  4,3M     0 100% /snap/gnome-calculator/536
/dev/loop19             squashfs   15M   15M     0 100% /snap/gnome-characters/359
/dev/loop20             squashfs  3,8M  3,8M     0 100% /snap/gnome-system-monitor/107
/dev/loop9              squashfs  157M  157M     0 100% /snap/gnome-3-28-1804/91
/dev/loop4              squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/97
/dev/loop8              squashfs  4,3M  4,3M     0 100% /snap/gnome-calculator/544
/dev/loop13             squashfs   55M   55M     0 100% /snap/core18/1265
/dev/loop12             squashfs   15M   15M     0 100% /snap/gnome-characters/367
/dev/loop16             squashfs  3,8M  3,8M     0 100% /snap/gnome-system-monitor/111
/dev/loop5              squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/98
/dev/loop10             squashfs  157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop0              squashfs   55M   55M     0 100% /snap/core18/1279
/dev/loop7              squashfs   90M   90M     0 100% /snap/core/8213
tmpfs                   tmpfs     789M   12K  789M   1% /run/user/1000
/dev/loop3              squashfs   90M   90M     0 100% /snap/core/8268

```

Would it be safe to, without reboot, use QParted to decrease /home size and add it to / ? But then, what happens when another 100GB is lost? :(

---

### Post by Bashing-om on 2019-12-11
hikariws; Hello -

> 
/dev/sda3               ext4       98G   93G  762M 100% /


so, take a closer look at "/".
```

cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, (The "x" switch limits du to a single file system, in this case the root file system.)

[INDENT]my bit to try and help
[/INDENT]

---

### Post by Skaperen on 2019-12-11
what i do is keep a semi-big (about 64 MB) file in each file system that i can [COLOR=#0000cd][FONT=courier new]**rm**[/FONT][/COLOR] at any time (as root) to have a brief period of some available space.  i also do that as a user for some users, in their home directory.

some filesystems can also reserve a percentage for root, but that doesn't help much if a root process fills it up.

it is possible for the space filling object to be unviewable by having no directory links (has been [COLOR=#0000cd][FONT=courier new]**rm**[/FONT][/COLOR]'d) while still open.  if you find an oversized file that you don't need, don't **[COLOR=#0000cd][FONT=courier new]rm[/FONT][/COLOR]** it.  instead, _[COLOR=#0000cd]**truncate -s0**[/COLOR]_ it while hunting down what has it open ([COLOR=#0000cd][FONT=courier new]**lsof**[/FONT][/COLOR] being the tool for this).

---

### Post by hikariws on 2019-12-11
du reports the same thing as QDirStat... remember that /home is in another partition


```
$ sudo du -sx * | sort -n
du: cannot access 'proc/7994/task/7994/fd/4': No such file or directory
du: cannot access 'proc/7994/task/7994/fdinfo/4': No such file or directory
du: cannot access 'proc/7994/fd/3': No such file or directory
du: cannot access 'proc/7994/fdinfo/3': No such file or directory
0       dev
0       initrd.img
0       initrd.img.old
0       proc
0       sys
0       vmlinuz
0       vmlinuz.old
4       cdrom
4       lib64
4       mnt
4       share
4       srv
8       media
16      lost+found
36      root
48      snap
160     tmp
208     opt
1872    run
12272   sbin
12628   bin
19952   etc
165987  boot
1115536 lib
2367940 var
5859880 usr
18075760        home

```


QDirStat is easier to browse, and it shows CrashPlan's cache as the top spender, but it's still 2GB. The hole thing is 8,5GB, so I'm in odds position.


> **Skaperen said:**
> it is possible for the space filling object to be unviewable by having no directory links (has been rm'd) while still open. if you find an oversized file that you don't need, don't rm it. instead, truncate -s0 it while hunting down what has it open (lsof being the tool for this).


I remember that was a big file I deleted, I don't remember its size, I think it was some log. Could it be that's the case? How to fix it now then?


I couldn't understand the commands you talked about.

---

### Post by yancek on 2019-12-11
I'd start by taking a look at /var/log for some extremely large log files.  I"ve seen them 15GB or more.

---

### Post by TheFu on 2019-12-11
I'd start with a find command to find really big files and start deleting.  There's a reason to keep the OS on a separate partition.  Generally, / with 25G should be enough. Then have /home/ on a different partition.

Anyways, 
**sudo find / -type f -size +5G -print** will find all the files of 5GB and larger.  There could easily be a log file in ~/ or /var/log/ that hasn't been properly pruned - or a core file left over from something.

Just make the size smaller and smaller as you slowly clean up unwanted huge files.

Then I'd circle back around using **du -sh** to look for specific subdirectories eating too much storage.  A common issue is if you play with virtual machines and forget to remove the old VM storage.

---

### Post by rsteinmetz70112 on 2019-12-13
If you find any really large log files you may want to investigate them to see what is causing them to get so large. I've had run away processes fill var to overflowing as fast as I could delete the files.

---

### Post by hikariws on 2019-12-16
Well I rebooted and now I have 84GB available... odd but I think it's solved.

---

