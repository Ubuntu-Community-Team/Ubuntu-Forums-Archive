---
title: "Main partition keeps being 100% full"
date: 2008-11-24
forum: General Help
---

### Post by BWPanda on 2008-11-24
I'm getting error messages telling me there's no disk space left.
a 'df -h' gives the following:
> Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              29G   29G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  212K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  3.0M  1.5G   1% /dev
tmpfs                 1.5G   24K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda2              77G   50G   24G  68% /home
/dev/sda3              20G  4.3G   15G  24% /windows
/dev/sdb1             146G   59G   81G  43% /media/disk-1

This happened the other night, so I resized the '/' partition to have about 10GB free space (which took hours), but the next day, it's 100% full again!

Any idea why this is happening and how to stop it?

---

### Post by CatKiller on 2008-11-24
The Disk Usage Analyser (gksudo baobab) will show you where the space is being used. I suspect /var/log has some large log files in. As to what's causing the disk usage, that depends on which directories are getting full. If it's a log file that's getting large you'll need to look at it and see which entries are getting added a lot.

---

### Post by Xiangxianni on 2008-11-24
> **CatKiller said:**
> The Disk Usage Analyser (gksudo baobab) will show you where the space is being used. I suspect /var/log has some large log files in. As to what's causing the disk usage, that depends on which directories are getting full. If it's a log file that's getting large you'll need to look at it and see which entries are getting added a lot.

Agree,
you can "su -s"--->then"du -sk *" to find which directory is the biggest---->then cd to that directory to "du -sk *" again.step by step you can find which files caused the issue.

---

### Post by drs305 on 2008-11-24
Large or numerous log files can be one reason, another could be if your trash bins are full - not only user trash but system trash as well. Emptying your user trash does not eliminate root's trash. If you have deleted large or numerous files recently, take a look at this link for finding and removing deleted files from your system:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by BWPanda on 2008-11-25
Thanks Xiangxianni, I used your suggestion to find a rather large 'disk' folder in '/media/' that had a few recent backups of my home directory. Turns out my External HD is located at 'disk-1'...

So I told my backup program where to backup to (disk-1, not disk), and everything should be fine!
Thanks for the help!

---

