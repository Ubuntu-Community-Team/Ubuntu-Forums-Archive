---
title: "Unable to install upgrades due to disk size"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by civitas on 2009-06-30
I am new to linux and ubuntu in particular. I have an HP Pavillion dv7 laptop that I have tried to dual boot with some help from my brother-in-law (a great guy) who did not have the time to stay around and encounter the following problem:

The laptop disk was structured as follows before the ubuntu 9.04 installation:

Windows Vista 64bit home on C:
Data designated on D:
Vista Recovery on E:

I believe ubuntu was installed on D: and I had no problems because this was a new laptop and I had no data on that partition.


Everthing seemed to work in ubuntu except when the auto update feature kicked in, I got the following error message:

[COLOR=Navy]- NOT ENOUGH FREE DISK SPACE

The upgrade needs a total of 356M free disk space on "/".  
Please free at least an additional 246M of disk space on "/".  
Empty you trash and remove temporary packages of form installations
sudo apt-get clean"
[/COLOR]
I did this to no avail.  However, using acronis in windows, I determined the linux installation was almost 3 gigs with a small swap file but the D: drive was virtually untouched.


Reading the forums, I did the command sudo fdisk -l with the following results:

[COLOR=Navy]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x877d3b07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28693   230473728    7  HPFS/NTFS
/dev/sda2           28693       30401    13720576    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x496a314e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30075   241577406    7  HPFS/NTFS
/dev/sdb2           30076       30401     2618595    5  Extended
/dev/sdb5           30076       30379     2441848+  83  Linux
/dev/sdb6           30380       30401      176683+  82  Linux swap / Solaris
[/COLOR]

Any suggestions for this linux ubuntu newbie?

Thanks in advance,

Civitas

---

### Post by merlinus on 2009-06-30
From what I can see, you have two hdds, sda and sdb.  Looks like vista is on sda1, with what probably is a recovery partition on sda2.

Linux is in a logical partition on the second hdd, sdb5, and indeed there does not appear to be much room on it.  sdb1 appears to be your data partition.

Remember that linux does not use letters for drives.

Run this in a terminal and post results:

```
df -h
```

---

### Post by civitas on 2009-07-01
Here are the results from command: df -h


[COLOR=Navy]Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             2.3G  2.1G   92M  96% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  100K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  176K  1.4G   1% /dev
tmpfs                 1.4G  596K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
[/COLOR]

Thanks in advance for all your help.

Civitas

---

### Post by raymondh on 2009-07-01
> **civitas said:**
> Here are the results from command: df -h


[COLOR=Navy]Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             2.3G  2.1G   92M  96% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  100K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  176K  1.4G   1% /dev
tmpfs                 1.4G  596K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
[/COLOR]

Thanks in advance for all your help.

Civitas

Hello Civitas,

As you can see, your Ubuntu root (/) is full.  Consider root as your 'main' ubuntu system files. A standard ubuntu install will be about 3-4GB in size, after the initial updates.  Most consider 8-15 GB a good size for ubuntu root.  I use 20GB as I tend to grow my system fat.  This does not include my personal data, settings, etc.

You may try deleting system trash to make some room ... but you may soon encounter another 'NO SPACE' problem soon.  Try, in terminal ..

```
sudo apt-get autoclean
```

or read this link for tips

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)


Another option is to free up some space in the data partition you have and the enlarge sdb2 to take up the freed space.

[http://www.howtoforge.com/linux_resizing_ext3_partitions_p2](http://www.howtoforge.com/linux_resizing_ext3_partitions_p2)

My best option is to start from scratch....If possible (with personal files saved elsewhere in the meantime).  With this, I can now set new parameters as well as partitions (separate /home, /usr, etc) and thus miminimize problems in the future.

Decide how you wish to proceed and Post back if you need assistance ....

---

