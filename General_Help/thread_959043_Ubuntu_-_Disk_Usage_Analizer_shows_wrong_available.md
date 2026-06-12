---
title: "Ubuntu - Disk Usage Analizer shows wrong available space"
date: 2008-10-26
forum: General Help
---

### Post by alfonsoglezz on 2008-10-26
Hi Everyone.

I've been using Ubuntu for quite some time now. So far, I've been able to resolve all my Ubuntu issues by investing some time in this forums. 
This is my first time posting. I have been trying to fix this issue and so far I can't seem to find a solution to my problem.

I have a 160GB hard drive. Disk Usage Analyzer says "Total File System Capacity 147.4 GB (used: 135.8 GB available 11.6 GB)". After clicking "Scan File System" the result comes back showing that I am only using 42 GB (which Is correct). Now I have done several things to try to fix this. So far this is what I have done:

- I forced a filesystem check at boot up.. No errors.
- Gparted says the same thing as File System Analizer (regarding space available - 98% full)
- df output:

alfonsoglezz@Ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             148G  136G  4.2G  98% /
varrun               1010M  232K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   40K 1010M   1% /dev
devshm               1010M   12K 1010M   1% /dev/shm
lrm                  1010M   39M  971M   4% /lib/modules/2.6.24-21-generic/volatile

Now, I should have about 105 GB of available disk space and not 4.2 GB. Hopefully someone knows how to fix this so Ubuntu can show the correct amount of used/free disk space.

Thank You!

---

### Post by ludovic.ferre on 2010-06-06
This sounds like a very old thread but I have the exact same problem!

My root partition is on /dev/sdd1 (SDD is a 250G SATA, SDD1 is 50G) and is shown by gparted, df or System Monitor to be 86% full (40.3GiB used, 6.5GiB free).

Here's a result from df running as root:

[INDENT]```
root@ub-x64:~# df /dev/sdd1 -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdd1               53G    44G   7.0G  87% /
```
[/INDENT]

Still running baobab I can see on root that 8.4GiB or in use, so I would be very interested to find out where the data is gone...

I am using the server as a samba file share for a lot of virtual machines running on the system. Really odd.

---

### Post by ludovic.ferre on 2010-07-11
Problem solved!

I found a few threads pointing to mounted drives or folder preventing users from seeing existing files on the root file system.

This was the case for me. I had a folder where I mount one of my SATA disk partition containing a Virtual Box machine backup. This was taking most of the space. After I unmounted the drive I could see the files and move them out to another location.

All is fine since!

---

### Post by salemboot on 2010-12-12
~/.gvfs mounts are getting reported in user's home directories.  

I'm still investigating this problem myself because 'df' is reporting 80% usage but I can only account for %10 of total disk usage. :KS

Update:
Ran the command 'du' as root; same results.
FSCK the drive partition letting it fix various items; same results.
Deleted my home directory; Freed up space.

Prognosis:
  File-system corruption.

System:
AMD64 Ubuntu 10.04 updated 2-weeks ago.
Ext4 with no barriers enabled.

Facts to note:
 There was no power cycle before the problem was noticed.  Gnome informed me there was a lack of space.

Resolution:
 Deleted my home directory.  It may be the fact I'm running no barriers ie. barrier=0 as the mount option in fstab.

---

