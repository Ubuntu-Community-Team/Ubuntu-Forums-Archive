---
title: "harddrive full? i think not!"
date: 2005-12-01
forum: General Help
---

### Post by dezibel on 2005-12-01
Hi there!

I'm running a ubuntu server-install as webserver, torrentbox and myth-box.

Strange error just recived;
it tells me that the disk mounted on /myth is full, but as you can se from "df -h";

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  4,5G   30G  13% /
tmpfs                 125M     0  125M   0% /dev/shm
tmpfs                 125M   13M  113M  10% /lib/modules/2.6.12-9-k7/volatile
/dev/hdb4             170G  112G   59G  66% /myth
/dev/sda1             230G  159G   60G  73% /media/lacie
/dev/hdb1             3,8G  2,7G  989M  73% /mnt/olddisk
```

why am i getting this error?

thanks for a great linux-distro, and a perfect forum btw :)

---

### Post by ape on 2005-12-01
You may have run out of inodes rather than disk space.

What does the output of `df -i` state for the number of free inodes for that partition?

NOTE: if you are using reiserfs, `df -i` will report no inodes free and no used inodes.

If you have indeed run out of inodes, the only way I know of fixing this is to back up your data and reformat the partition specifying a higher number of inodes.

---

### Post by dezibel on 2005-12-01
okei...
I'm guessing inodes means something like nr of files?

```
thomas@myth-ubuntu:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/hda1            4791136  160613 4630523    4% /
tmpfs                  31973       1   31972    1% /dev/shm
tmpfs                  31973      17   31956    1% /lib/modules/2.6.12-9-k7/volatile
/dev/hdb4              43392   43392       0  100% /myth 
/dev/sda1           30539776  102729 30437047    1% /media/lacie
/dev/hdb1             409696  134281  275415   33% /mnt/olddisk
```

how do i reformat with more inodes? is there a better filesystem than ext3 for me?

---

### Post by Drain on 2005-12-02
[QUOTE=dezibel]
how do i reformat with more inodes? is there a better filesystem than ext3 for me?[/QUOTE]

I'm not sure how to reformat your disk to have more inodes, but I recalled that [Jarod Wilson's Guide]("http://wilsonet.com/mythtv/fcmyth.php") to setting up MythTV on Fedora, and the mythtv.org documentation both suggested using XFS or JFS for MythTV's partition.  Back up you data and try to reformat it.

---

### Post by ape on 2005-12-02
To reformat with more inodes using mkfs.ext2, you would need to pass the -N argument with the number of inodes that you want to create.  You also need to ensure that you set the inode block size appropriately for the average size of the files that exist on your /myth partition.

As Drain mentioned, you should probably make use of one of the Myth-recommended filesystem types.  Some of these filesystems don't have a fixed number of inodes as ext2 does, so you won't get this type of error.

---

