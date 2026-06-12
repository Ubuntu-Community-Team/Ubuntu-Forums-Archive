---
title: "[SOLVED] &amp;quot; / &amp;quot; Partition vs &amp;quot; / &amp;quot; Properties"
date: 2008-08-15
forum: General Help
---

### Post by greenco on 2008-08-15
I am trying to get my head around what the Ubuntu 8.04 folders are for. When I run Gparted it shows that the partition for my " / " section as being 18.63 GB, with 2.46 GB used and 16.17 GB unused.
 
When I open the filesystem to display the folders that are in the " / " folder, the properties screen shows that it contains 196,412 items and takes up 49.7 GB. 

According to properties screen, the size of the " / " is 2.66 times bigger then the whole partition. Is this normal?

What folders are included in the "2.46 GB used" portion of the partition?

I can store the 2.46 GB of data on a DVD, but I can not store the 49.7 GB on one.

Thanks

---

### Post by mikewhatever on 2008-08-15
Linux directory structure is outlined in the links below:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://geek2live.blogspot.com/2007/09/linux-file-structure.html](http://geek2live.blogspot.com/2007/09/linux-file-structure.html)
[http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/](http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/)

Not sure if you need all of them.

If your / directory is shown larger then it actually is, it's not normal, but to verify what's the case, post the output of **df -h** command here.

---

### Post by Oldsoldier2003 on 2008-08-15
do you have a separate home or data partitions? GParted reports the size of individual partitions when you look at the properties of / Nautilus it will report the contents of the entire Linux file hierarchy regardless of what partition the files reside upon.

---

### Post by Oldsoldier2003 on 2008-08-15
> **mikewhatever said:**
> Linux directory structure is outlined in the links below:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://geek2live.blogspot.com/2007/09/linux-file-structure.html](http://geek2live.blogspot.com/2007/09/linux-file-structure.html)
[http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/](http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/)

Not sure if you need all of them.

If your / directory is shown larger then it actually is, it's not normal, but to verify what's the case, post the output of **df -h** command here.

although some people backup the entire system a good backup really only needs to be of your data and configurations. sure it takes a little longer to reinstall applications  but that can be easily automated as well.

---

### Post by greenco on 2008-08-15
mikewhatever, thanks for the links. I have bookmarked them for future references.

Oldsoldier2003, my hard disk is partitioned as follows:

/      18.63 GB   2.46 GB used   16.17 GB unused
/home  208.62 GB   46.96 GB used   159.65 GB unused 
/swap  5.58 GB

---

### Post by cariboo on 2008-08-15
When using the graphical Disk Usage Analzer it also includes .gvfs size in the total. I always use in a terminal:

```
df -h
```

Because it seem the graphical apps lie a lot of the time.

Jim

---

### Post by greenco on 2008-08-15
cariboo907

Here is the results of your idea. What does it tell me?

coleman@coleman-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.4G   16G  14% /
varrun               1013M   92K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   64K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  974M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             207G   48G  150G  25% /home
gvfs-fuse-daemon       19G  2.4G   16G  14% /home/coleman/.gvfs

---

### Post by jerome1232 on 2008-08-15
It tells me that nautilus thinks that 48GB+2.4GB=49GB lol

But oldsoldier was correct, Nautilus doesn't care about partitions, it's showing the entire Linux hierarchy and totaling it. /home being under / is included.

Gparted shows them by partition, as / and /home are on different partitions it's totaling them separately

---

### Post by bingoUV on 2008-08-15
Are you looking to solve some problem, or this question is for curiosity?

As you have figured out by now, / is the "root" directory. All other directories are "inside" /. You have /home on another partition. From the file/directory hierarchy point of view, /home is "inside" /. So disk usage of / includes the disk usage of /home. This is the point of view of the "du" command.

But as /home comes from another partition, from a partition point of view the data in /home is "outside" /. This is the point of view of the "df" command.


EDIT: To figure out exactly which folders (directories) are under /, do the following.
```

mkdir /tmp/slash
sudo mount --bind / /tmp/slash

```

Now browse /tmp/slash using nautilus or whatever. This is the stuff that comes from the partition which is mounted on /.

---

### Post by mikewhatever on 2008-08-15
> **Oldsoldier2003 said:**
> although some people backup the entire system a good backup really only needs to be of your data and configurations. sure it takes a little longer to reinstall applications  but that can be easily automated as well.

Have I said otherwise?

---

### Post by victor.zamanian on 2008-08-15
> **bingoUV said:**
> Are you looking to solve some problem, or this question is for curiosity?

As you have figured out by now, / is the "root" directory. All other directories are "inside" /. You have /home on another partition. From the file/directory hierarchy point of view, /home is "inside" /. So disk usage of / includes the disk usage of /home. This is the point of view of the "du" command.

But as /home comes from another partition, from a partition point of view the data in /home is "outside" /. This is the point of view of the "df" command.


EDIT: To figure out exactly which folders (directories) are under /, do the following.
```

mkdir /tmp/slash
sudo mount --bind / /tmp/slash

```

Now browse /tmp/slash using nautilus or whatever. This is the stuff that comes from the partition which is mounted on /.

Well put.

---

### Post by greenco on 2008-08-15
victor.zamanian
It was mainly out of curiosity. I believe I now have a grasp on how it works. If I total up all of the folders in the " / " folder it adds up to about 2.9 GB. I can put all of these folders onto a flash drive for backup purposes.

I thank everyone for their help!!!

---

### Post by victor.zamanian on 2008-08-18
> **greenco said:**
> victor.zamanian
It was mainly out of curiosity. I believe I now have a grasp on how it works. If I total up all of the folders in the " / " folder it adds up to about 2.9 GB. I can put all of these folders onto a flash drive for backup purposes.

I thank everyone for their help!!!

Oh, no, I didn't mean it was well put asking if you wanted to solve a problem or if you're just asking out of curiosity, I just agreed with everything he explained. :-)

---

