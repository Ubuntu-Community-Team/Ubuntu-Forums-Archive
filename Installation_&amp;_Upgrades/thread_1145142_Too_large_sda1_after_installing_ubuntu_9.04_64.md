---
title: "Too large /sda1 after installing ubuntu 9.04 64"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by captain_rob on 2009-05-01
Hi there,

I made a fresh install of ubuntu 9.04 and I see now that my sda1 (ext4) is too large. 

This is my df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19228276  13213236   5038292  73% /
tmpfs                   951992         0    951992   0% /lib/init/rw
varrun                  951992       224    951768   1% /var/run
varlock                 951992         0    951992   0% /var/lock
udev                    951992       140    951852   1% /dev
tmpfs                   951992        96    951896   1% /dev/shm
lrm                     951992      2760    949232   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2            286449880   4712776 267186232   2% /home

Whats my problem and how to solve this without reinstalling?

---

### Post by taurus on 2009-05-01
What do you mean your /dev/sda1 is too large because you have already used up 73% of disk space on /dev/sda1?

---

### Post by captain_rob on 2009-05-01
Yes you are right, 73% is used of almost 20 GB. That seems too much. If I used the disk analyzer I cannot find what is using so much.

Please help.

---

### Post by taurus on 2009-05-01
```
sudo du -h /root
sudo du -h /var
```

---

### Post by captain_rob on 2009-05-01
I actually did du -sm * | sort -nr | head -10

This is the result

root@rob-desktop:/# du -sm * | sort -nr | head -10
du: cannot access `home/rob/.gvfs': Permission denied
du: cannot access `proc/3997/task/3997/fd/3': No such file or directory
du: cannot access `proc/3997/task/3997/fdinfo/3': No such file or directory
du: cannot access `proc/3997/fd/3': No such file or directory
du: cannot access `proc/3997/fdinfo/3': No such file or directory
9185	root
4364	home
2781	usr
342	var
132	lib
104	opt
15	etc
14	boot
11	lib32
10	sbin


Any idea?

---

### Post by drs305 on 2009-05-01
Take a look at the guide linked to in my signature line about finding lost disk space. It is pretty comprehensive and will probably be able to help you find where your free space has gone.

---

### Post by captain_rob on 2009-05-01
Thank you very muuch guys for your response. I found the problem already, I didn't expect and overlooked (stupid me) a directory named 'Elements' in the .Trash directory of root. There I found deleted files from the external drive. How can I prevent that deleted files from the external harddisk are stored there in future?

---

