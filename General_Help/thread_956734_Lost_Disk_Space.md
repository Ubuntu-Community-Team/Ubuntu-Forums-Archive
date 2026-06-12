---
title: "Lost Disk Space"
date: 2008-10-23
forum: General Help
---

### Post by thecircusb0y on 2008-10-23
Hey Guys, I have a major problem. 
My ubuntu 8.04 desktop has a 400gb Harddrive. 
100gb goes to / (root)
1gb goes to SWAP
the rest (about 297) goes to /home/

The weird thing is that home is reporting to be full, and its only using 13.5 gb. 

Does anybody know whats going on?

---

### Post by phidia on 2008-10-23
If you open a terminal and enter > fdisk -l what does that show?

---

### Post by thecircusb0y on 2008-10-23
> **phidia said:**
> If you open a terminal and enter  what does that show?
sudo fdisk -l yields:
> 
Disk /dev/sda: 400.0 GB, 400088457216 bytes

255 heads, 63 sectors/track, 48641 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xee534eba



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       12158    97659103+  83  Linux

/dev/sda2           12159       12326     1349460   82  Linux swap / Solaris

/dev/sda3           12327       48641   291700237+  83  Linux



Disk /dev/sdb: 2040 MB, 2040528896 bytes

29 heads, 28 sectors/track, 4908 cylinders

Units = cylinders of 812 * 512 = 415744 bytes

Disk identifier: 0x00000000



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        4909     1992580+   6  FAT16



---

### Post by geirha on 2008-10-23
What's the output of this command? ```
df -h
```

Also, where does it report that it ony uses 13.5GiB? Have you looked at Applications -> Accessories -> Disk Usage Analyzer?

---

### Post by thecircusb0y on 2008-10-28
df -h results 
> thecircusb0y@blackbox:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/sda1              93G   35G   53G  40% /

varrun                1.9G  228K  1.9G   1% /var/run

varlock               1.9G     0  1.9G   0% /var/lock

udev                  1.9G   64K  1.9G   1% /dev

devshm                1.9G  260K  1.9G   1% /dev/shm

lrm                   1.9G   44M  1.8G   3% /lib/modules/2.6.24-21-generic/volatile

/dev/sda3             276G  254G  8.8G  97% /home

gvfs-fuse-daemon       93G   35G   53G  40% /home/thecircusb0y/.gvfs

/dev/sdb1             2.0G     0  2.0G   0% /media/disk



I deleted some things to free up the space it allows me. So Disk Usage Analyzer says Filesystem capacity is 462.7 GB(Used:322.8GB Available:139.9GB)
That doesn't make sense, Its a fresh desktop install of ubuntu 8.04, with an installation of srcds for running a zombie panic server, and a few files. theres no way I'm using 322 gb's. 
also if I goto Places-> Home Folder, the status bar at the bottom says freespace: 8.8gb .

---

### Post by thecircusb0y on 2008-10-28
Okay Guys, Nevermind, I figured out the problem. 

For some reason , the trash can was said to be empty by Ubuntu, but I did alittle Sudo Nautilus and set true to view hidden files. Looked in the home directory and there was a trash folder with a ton of "deleted" files from a transfer I did a few weeks ago. So I'm just deleting that folder, and I should be fine. Thanks alot for the help, your attention, your time, etc. I'm so glad to free up this space, I really need it.

---

