---
title: "my hard drive is full, how?"
date: 2008-09-06
forum: General Help
---

### Post by terry f on 2008-09-06
I just got an eee pc last week and installed Ubuntu on it.  Ubuntu is installed on a 9.3GB partition and /home is mounted to a like 20GB partition.  For some resion the Ubuntu partition is now full.  Does any one know why it would be so full and how to empty up some space.  The only thing I installed on it other what came one it was JDK, bluej, freeNX, exaile, and VLC.

---

### Post by ~LoKe on 2008-09-06
In a terminal type..
```
df -h
```
So we can see where the space is going.

---

### Post by terry f on 2008-09-06
df -h output
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             8.1G  7.7G     0 100% /
varrun                502M  220K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   64K  502M   1% /dev
devshm                502M   12K  502M   1% /dev/shm
/dev/sdb2              22G  630M   21G   3% /home
overflow              1.0M   32K  992K   4% /tmp
gvfs-fuse-daemon      8.1G  7.7G     0 100% /home/terry/.gvfs
/dev/sdc1             1.9G  708M  1.2G  37% /media/disk

```

---

### Post by mb_webguy on 2008-09-06
Open Applications->Accessories->Disk Usage Analyzer, and click the Scan Filesystem button.  Be patient, because this might take a while.  Once it's done, you should be able to identify which files are taking up all of your disk space.

Personally, I like KDirStat better than Ubuntu's default disk usage analyzer tool, but since your drive is full you probably won't be able to install it without cleaning up the drive first.

---

### Post by terry f on 2008-09-07
well what ever is in the root of /var/log is taking up like 5GB, and its not the sub folder just the root.

the big files are:
```
syslog.0 @ 1.7GB
messages.0 @ 1.7GB
kern.log.0 @ 1.7GB
```

---

### Post by hyper_ch on 2008-09-07
they shouldn't be nearly as big... somethings wrong with those logs.

---

### Post by terry f on 2008-09-07
What can I do to fix them?

---

### Post by hyper_ch on 2008-09-07
Hmmm, actually it's quite simple it seems:

(1) edit logrotate config (logrotate is the daemon that controls the rotating of the log files)

```

sudo nano /etc/logrotate.conf

```

(2) change
- weekly to daily
- logrotate 4 to logrotate 1

(3) exit and save logrotate.conf
by pressing ctrl-x, "y", "enter"

(4) force a manual logrotate with the new settings
```

sudo logrotate -f

```

That should clear those files out.

---

### Post by terry f on 2008-09-07
sudo logrotate -f does not work on the big files the ones named *.log.0 it does work on the *.log but they are not very big.

---

### Post by hyper_ch on 2008-09-07
then delete the .0 ones manually... also .1 and .2 and .3 ....

---

### Post by dioltas on 2008-09-07
Just delete the .log.0 files? Thats what i'd do, but maybe that's a bit reckless. :D
They are only logs after all. The way they're named .log.0 would make me think their just copies or backups.

Could be very wrong though...

Edit: ya, hyper_ch got in there before me

---

### Post by hyper_ch on 2008-09-07
> **dioltas said:**
> Edit: ya, hyper_ch got in there before me

That happens all the time... sometimes you're quicker, sometimes others ;) it's the effort that counts.

---

### Post by terry f on 2008-09-07
That worked thanks, now there is a lot of room.  Any idea what would make that happen?

---

### Post by hyper_ch on 2008-09-07
for that you would have been required to have a look at the logs  ;)

my largest log file is 5mb.

---

