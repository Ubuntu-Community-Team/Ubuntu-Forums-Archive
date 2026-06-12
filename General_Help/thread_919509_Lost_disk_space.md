---
title: "Lost disk space"
date: 2008-09-14
forum: General Help
---

### Post by thomasyen on 2008-09-14
Hello everybody.
Recently, I discovered that my available disk space had decreased significantly, from 12 GB to 2 GB in three to four days. I didn't do anything that used up remotely that much space. The size of my root partition is approximately 43 GiB, but when I used Disk Usage Analyzer and added up all the file sizes, I got approximately 15 GiB. GParted on the other hand showed 43.87 GiBs of used space and 4.58 GiBs of unused space. Where did the other 10 GB go and why is there such a difference between analyses? A few months ago I had the exact same problem, but a few weeks after the problem occurred, the lost space magically came back. Can anyone give a hint as to why?
(p.s. I looked in other threads named "lost disk space" and tried everything suggested, but nothing worked.)

---

### Post by mudbrickcreative on 2008-12-16
I'm seeming to have the same problem. The numbers just dont add up for the size of the disk and what is on it. xdiskusage returns back 11gig Permission Denied. Not sure if you've run that to see what it says (make sure you run it as root though). My df -h reports back

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   29G  4.7G  87% /
varrun               1014M  1.2M 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   72K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
/dev/sdb1             147G   79G   61G  57% /backup
/dev/md0              917G  224G  648G  26% /share

I used baobab to check out the size of all my files and I can't come up with 29G on sda1. 

Anyone have some ideas?

---

### Post by dabl on 2008-12-16
In the console, 

```
sudo du -h max-depth=1
```

This will show how much is used for each top-level directory. Then you can see where the space is being taken.

---

### Post by drs305 on 2008-12-16
I also use the "df -h" command to inspect partition usage. If you want to run the one from the previous post, try: " sudo du -h --max-depth=1 "

The most likely cause is either large backup files that ended up in the wrong place or you have a large amount of trash in either the user or root accounts. Take a look at this link for how to find and inspect your trash bins and how to find large files that might be taking up a lot of space:
[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by mudbrickcreative on 2008-12-16
53M     ./boot
6.5M    ./sbin
4.0K    ./share2
0       ./proc
16M     ./etc
0       ./sys
4.0K    ./mnt
224K    ./dev
4.3M    ./tmp
16K     ./lost+found
3.5M    ./bin
79G     ./backup
4.0K    ./srv
16K     ./media
4.0K    ./opt
216M    ./lib
11G     ./home
4.0G    ./var
480K    ./root
64M     ./install
4.0K    ./initrd
223G    ./share
2.4G    ./usr
319G    .


Thats the output from du. If you do a little math 319 - 223 - 79 = 17. (/share and /backup are on different disk). I should be using 17 gig of my 36 gig drive. While df says I'm using 29 gig. So where is the extra 12 gig going? There are inodes and the reserved root space but there is no way that should be 12 gig.

PS I looked into the trashes but there aren't any. I use the system remotely 99% of the time over ssh with X.

---

### Post by Polygon on 2008-12-16
that is weird. the reserved root space is 5% by default and that should be around 1.8 gb, so there is still 11.2 that is unaccounted for. 

are you sure that you have the entire disk partitioned? i had a problem where my disk was showing an incorrect size and it was because the partition was borked and it wasn't filling up the entire partition, and i think running repair/check (not sure, im not on linux at the moment) on that partition seemed to fix it

---

### Post by jerome1232 on 2008-12-16
The only way I can reproduce this is like this:

1) copied 1.5 GB to /mnt
2) Mounted my external disk at /mnt
3) Now I have discrepancies while the media is mounted in what my tools are telling me

In the first example my numbers agree
```
# pre mount, from "sudo du -h --maxdepth=1 /"
0	/proc
19G	/opt
16K	/lost+found
14M	/etc
448M	/lib
7.9M	/bin
[COLOR="Lime"]1.4G	/mnt[/COLOR]
663M	/var
8.9M	/sbin
101G	/home
4.0K	/srv
4.5G	/usr
8.0K	/media
44M	/root
0	/dev
80K	/tmp
0	/sys
53M	/boot
4.4M	/lib32
[COLOR="Lime"]127G	/[/COLOR]
# and from "df -h"
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Lime"]/dev/sda1             228G  127G   90G  59% /[/COLOR]
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  336K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  656K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
```

Now let's mount my external; You'l notice the numbers don't agree this time
```

sudo mount /dev/sdb1 /mnt
sudo du -h --max-depth=1 /
0	/proc
19G	/opt
16K	/lost+found
14M	/etc
451M	/lib
7.9M	/bin
[COLOR="Red"]12G	/mnt[/COLOR]
664M	/var
8.9M	/sbin
101G	/home
4.0K	/srv
4.5G	/usr
8.0K	/media
44M	/root
3.5M	/dev
80K	/tmp
0	/sys
53M	/boot
4.4M	/lib32
[COLOR="Red"]137G	/[/COLOR]
# now df
sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda1             228G  127G   90G  59% /[/COLOR]
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  336K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  668K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             150G   13G  138G   9% /mnt
```

137-12=125, while df shows (correctly) 127

Is it possible that files have been written to /backup and/or /share while they where unmounted? Try unmounting them and check if there's still any files there.

---

### Post by mudbrickcreative on 2008-12-16
that did it jerome1232. The backup drive was off line last week. The backup must have run once or twice before I got it fixed. Why isn't there a way to see this normally? Seems to be an weakness in how the file structure is handled. I will be more careful in the future.

---

### Post by dabl on 2008-12-16
> **mudbrickcreative said:**
> 

4.0G    ./var



That's about 10x what it should be, too.  You don't need the logs from 1993 any more.  :lolflag:

---

### Post by mudbrickcreative on 2008-12-16
> **dabl said:**
> That's about 10x what it should be, too.  You don't need the logs from 1993 any more.  :lolflag:

No just my MySQL logs for the past few weeks, probably should turn them off.

---

