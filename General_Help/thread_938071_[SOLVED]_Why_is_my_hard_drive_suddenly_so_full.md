---
title: "[SOLVED] Why is my hard drive suddenly so full?"
date: 2008-10-04
forum: General Help
---

### Post by josephellengar on 2008-10-04
For the longest time my Hardy installation and all other parts took up only 8gb of the 30gb partition that I gave it.  The other day I increased the partition size to 50gb.  Now, my Hardy installation is taking up 23gb.  This is a big problem because my external hard drive that I back up to is only 40gb and I need to image three separate hard drives onto it.  Any suggestions or explanations for this strange behavior?  Thanks!

---

### Post by fooman on 2008-10-04
in ubuntu,  you can go to applications > accessories > disc usage analyzer 

in the toolbar choosing "scan filesystem" will give a complete breakdown of where things are stored.  or you can choose a specific directory to scan.

that should give you a good idea of exactly where the buildup is occurring.

---

### Post by johncolescarr on 2009-08-04
> **idigchess said:**
> For the longest time my Hardy installation and all other parts took up only 8gb of the 30gb partition that I gave it.  The other day I increased the partition size to 50gb.  Now, my Hardy installation is taking up 23gb.  This is a big problem because my external hard drive that I back up to is only 40gb and I need to image three separate hard drives onto it.  Any suggestions or explanations for this strange behavior?  Thanks!

I am experiencing similar.  Since installing 9.04 by HDD has completely filled up to 95%.  Checking with the disk usage analyser, my entire file system is 25GB but my ubuntu partition is 60GB, whats taking up the space??!!

Can someone help me as its bringing me close to system crash

---

### Post by philinux on 2009-08-04
Post the output of this

```
df -h
```

See this link.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by q_mar on 2009-08-23
I have the same problem.

I have an 80 GB hard drive which is now completely full.

Df -h States:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G   72G     0 100% /
tmpfs                 494M     0  494M   0% /lib/init/rw
varrun                494M  344K  493M   1% /var/run
varlock               494M     0  494M   0% /var/lock
udev                  494M  136K  493M   1% /dev
tmpfs                 494M   84K  493M   1% /dev/shm
lrm                   494M  2.2M  491M   1% /lib/modules/2.6.28-14-generic/volatile
overflow              1.0M   28K  996K   3% /tmp

Yet when i use the Disk usage analyzer it states that there is a total of 3gb in / but yet somehow mysteriously 71.3 of 71.3 GB are used.

Any Ideas?

---

### Post by AmerNewbieInDE on 2009-08-23
> **q_mar said:**
> I have the same problem.

I have an 80 GB hard drive which is now completely full.

Df -h States:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G   72G     0 100% /
tmpfs                 494M     0  494M   0% /lib/init/rw
varrun                494M  344K  493M   1% /var/run
varlock               494M     0  494M   0% /var/lock
udev                  494M  136K  493M   1% /dev
tmpfs                 494M   84K  493M   1% /dev/shm
lrm                   494M  2.2M  491M   1% /lib/modules/2.6.28-14-generic/volatile
overflow              1.0M   28K  996K   3% /tmp

Yet when i use the Disk usage analyzer it states that there is a total of 3gb in / but yet somehow mysteriously 71.3 of 71.3 GB are used.

Any Ideas?

open your home folder, ctrl+h to show hidden files, look at .local/share/trash

i found out that stuff that i though i deleted and emptied trash, was actually still there. i was also told that the same happens to usbsticks.. everything uses its own trash.

---

### Post by q_mar on 2009-08-23
No Dice, That folder for all users was a total of 8.3KB. Thanks for the reply though.

---

### Post by michy99 on 2009-08-23
First a tip. If you post in a thread that says [SOLVED] in the topic, most people will pass it by because they won't realize that there is a new problem posted.

Now for your space problem, read this page and see if anything on it helps:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by q_mar on 2009-08-23
Thanks Very Much! I figured it out with some help from that link. Apparently it was storing the deleted files from one of my external drives on the OS Partition.

---

### Post by drs305 on 2009-08-23
For others who may frequent this thread, here is a link to a post which provides assistance in determining why a disk is suddenly full and how to fix it:
[Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

