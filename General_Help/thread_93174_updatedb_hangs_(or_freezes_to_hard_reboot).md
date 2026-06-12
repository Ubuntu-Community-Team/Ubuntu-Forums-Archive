---
title: "updatedb hangs (or freezes to hard reboot)"
date: 2005-11-21
forum: General Help
---

### Post by towsonu2003 on 2005-11-21
in a previous post, I mentioned that when cron launches updatedb, system either hangs (20-30 seconds) or freezes (hard reboot required). I found the way to edit that cron thing but:

even if I do

sudo nice -n 19 updatedb (to make it run at lower probability)

it still hangs (may freeze but probability is lower).

may this be related to HDD size (100GB) or updating NTFS (20GB + 30GB)  & Fat32 (1GB) partitions? I somehow found a way (forgot now, may be by editing /etc/updatedb.conf)) to exclude NTFS and current situation is: no more freezes, but may hang (lower probability)...

any help appreciated..

---

### Post by Xian on 2005-11-22
Just do some simple troubleshooting. First, narrow the scope of the search to only the Ubuntu system. Then if that runs okay, you can broaden it out a little to another partition if you really care about pulling in all of those additional files.

Alter the PRUNEPATHS line in /etc/updatedb.conf.

---

### Post by xavim on 2008-01-18
I have been experiencing the same problem (running Ubuntu
7.10 aka Gutsy, Desktop i386).

The following command:
```
$ sudo /usr/bin/updatedb
```
froze (and sometimes rebooted) my laptop.  The command
is run daily in /etc/cron.daily/slocate, so I was seeing the
freezes every day (quite annoying).

I traced it back to a corruption of  the / filesystem (which
uses ReiserFS).

Booting from a 7.10 installation CD and running the
following command:
```
 $ reiserfsck --rebuild-tree --logfile ~/Desktop/rebuild.log \
      /dev/PARTITION_DEVICE
```
solved the problem for me (updatedb does not hang any
more).

Hope that helps.

---

