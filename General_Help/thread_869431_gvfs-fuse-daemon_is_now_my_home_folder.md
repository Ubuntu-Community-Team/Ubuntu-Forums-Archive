---
title: "gvfs-fuse-daemon is now my home folder"
date: 2008-07-24
forum: General Help
---

### Post by natrone on 2008-07-24
What the heck is this gvfs-fuse-daemon and why is my home folder mounted to it?  I created my home folder on a 72GiB hard drive and it is indicating 61GiB free.  When I try to save a movie into for example /home/xxxx/videos it says I have only 1.5 GiB free.  WTH!

---

### Post by sdennie on 2008-07-24
It's the mechanism gnome uses to mount, for example, samba shares, so that they appear somewhat seamlessly within the environment.  If you run "df", you should see that it's mounted in /home/username/.gvfs and not your home directory. Posting the output of "df" here might be useful in figuring out your problem.

---

### Post by natrone on 2008-07-25
I will post the output of df as soon as I get home.

---

### Post by natrone on 2008-07-25
The output to df:

Filesystem           1K-blocks      Used Available Use% Mounted on

/dev/sdb2              6423120   4394224   1705188  73% /

varrun                  517428       100    517328   1% /var/run

varlock                 517428         0    517428   0% /var/lock

udev                    517428        60    517368   1% /dev

devshm                  517428        48    517380   1% /dev/shm

lrm                     517428     39760    477668   8% /lib/modules/2.6.24-19-generic/volatile

gvfs-fuse-daemon       6423120   4394224   1705188  73% /home/nathan/.gvfs

---

