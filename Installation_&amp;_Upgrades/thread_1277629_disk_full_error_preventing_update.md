---
title: "disk full error preventing update"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by bikeman1 on 2009-09-28
Hi -- I am not able to update because my root partition is listed as being full -- and seems to be.  I have a single root partion, plus a home partition.  Here is what is up.

myname@server:~/Desktop$ df -Th | sort
/dev/sda1     ext3     56G   55G     0 100% /
/dev/sda6     ext3     35G  1.7G   32G   6% /home
/dev/sdb1     ext2    1.1T  944G  101G  91% /mnt/Wilbur
Filesystem    Type    Size  Used Avail Use% Mounted on
lrm          tmpfs    438M  2.4M  436M   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1.0M   20K 1004K   2% /tmp
tmpfs        tmpfs    438M     0  438M   0% /lib/init/rw
tmpfs        tmpfs    438M  480K  438M   1% /dev/shm
udev         tmpfs    438M  160K  438M   1% /dev
varlock      tmpfs    438M     0  438M   0% /var/lock
varrun       tmpfs    438M  716K  437M   1% /var/run

I think (but am nit sure) that the overload is a backup file (from SimpleBackup) that went directly onto the hard drive rather than the raid array loaded in /mnt, oxccurring when /dev/sdb1 failed to mount.  But I can't find the offending file, and can't access the root trash even with gksudo nautilus.  I am sort of handcuffed.  My own trash (on the desktop) seems empty

Can anyone suggest a way for me to find the lurking trash and delete it ??  whenever I try to view the trash in nautilus, I encounter an error

Sorry, could not display all the contents of "trash": Operation not supported.

and the trash read operation just hangs.  

alternately, should I clean up some other filespace and then update?

I did chown permissions of the root trash and try deleting it.  No effect.  Acts like a permission issue

---

### Post by Arand on 2009-09-28
[https://help.ubuntu.com/community/find#Locating%20Files%20by%20Size](https://help.ubuntu.com/community/find#Locating%20Files%20by%20Size)
^Helps you find files by size

Alternatively you could use the "Search for files and folders utility from the places menu, which also has by-size filtering"
"Disk usage analyzer" under applications>accessories can be used to spot which folders are large
- Arand

---

### Post by Arand on 2009-09-28
And if you want to peek at the trash of root I would normally use a root terminal session:```
sudo -i
```and peek:```
ls -lah /root/.local/share/Trash/files
```If something offending is there:```
rm -ir /root/.local/share/Trash/*
```(this will also delete some nautilus metafiles related to the "trashed" files)
If you want to do it quick and dangerous skip the i (interactive) in -ir above.
 - Arand

---

### Post by bikeman1 on 2009-09-28
Arand, that sure fixed it (the interactive delete).  That goes into my book of Linux secrets.....

I understand why it happened, and can/should set up SimpleBackup to not backup onto /mnt when the raid is not loaded.  So hopefully it won't happen again

however, why, after it did happen and filled up the hard drive, was it blocking authentication efforts.  I was having problems with users-admin, update, various file access issues via nautilus, etc.  Was the disk just so full that buffers were unavailable for operations?

Also, I don't understand why deleted files go to the root trash and not the user trash.....

anyway thanks for your help!  Bailed me out big time

BM1:)

---

