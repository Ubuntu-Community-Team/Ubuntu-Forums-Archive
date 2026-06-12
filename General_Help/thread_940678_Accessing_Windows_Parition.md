---
title: "Accessing Windows Parition"
date: 2008-10-07
forum: General Help
---

### Post by ucal on 2008-10-07
Is there anyway that I can get ubuntu to access my windows partition?  I ask, because I would like to run a windows box on Ubuntu (any help on that would be awesome too), and I would like the box to access natively my windows files.  It also wouldn't hurt to be able to listen to all my music on the windows partition without having to transfer them gigabyte by gigabyte through my PSP.

---

### Post by Bucky Ball on 2008-10-07
Are you talking about two separate machines or one machine dual booting? Ubuntu will access NTFS, FAT drives no problem either way and you windoze partition should appear in Ubuntu automatically if you are talking about a dual boot. If not, you can network two machines and swap files that way.

---

### Post by ucal on 2008-10-07
Its a dual boot.  I haven't been able to find my windows partition though.

---

### Post by Tethylis on 2008-10-07
If its a dual boot configuration you should be able to go to Places > Computer > then there should be something there that shows your windows partition.

---

### Post by ucal on 2008-10-07
There are 3 folders in Computer.

CD RW/DVD+RW drive
OS
Filesystem

If I attempt to open OS, I get an unable to mount volume error. I don't think the windows partition is in the filesystem folder (in my experience so far, that has been strictly ubuntu).

---

### Post by Tethylis on 2008-10-07
I did a google search and found this 

[http://ubuntuforums.org/showthread.php?t=245691](http://ubuntuforums.org/showthread.php?t=245691)

It sounds like this user had the same problem. So hopefully this method will solve your problem too :)

---

### Post by geirha on 2008-10-07
OS sounds like it could be your windows drive. The reason it won't mount is probably that the filesystem hasn't been properly unmounted by windows. Try booting into windows and then reboot again into ubuntu. That should make it get unmounted properly. While you're in windows, run a scandisk too just to make sure it's not a filesystem error.

If you still can't access it after this, paste the output of these commands run in a terminal:
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by ucal on 2008-10-07
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       24113   183129088    7  HPFS/NTFS
/dev/sda4           24114       30402    50509673    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   82  Linux swap / Solaris
/dev/sda6           24114       29825    45881608+  83  Linux
/dev/sda7           29826       30074     2000061   82  Linux swap / Solaris

Partition table entries are not in disk order
adam@adam-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c2e0d163-eb45-47f2-b986-79a42d66ec2d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=0e687747-9d53-474f-b17e-c26bd7b90917 none            swap    sw              0       0
/dev/sda3       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

I have to go to class.  Be back in an hour or so.

---

### Post by geirha on 2008-10-07
Apparently your windows filesystems hasn't been added to fstab. Follow this [guide](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting partitions manually) to add them to your fstab. I'm guessing /dev/sda2 is your "C:" and /dev/sda3 is "D:" in windows.

---

### Post by ucal on 2008-10-07
That would make sense considering that it is an NTFS partition, but dev/sda3 is already in the fstab.  

```
/dev/sda3       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I followed the instructions on that site, and that is how I found this.  Maybe I'm doing something wrong though.  I also used a script from that site which mounted sda2, but that doesn't include most of my windows partition.  Just system specific stuff I think.

---

### Post by ucal on 2008-10-07
I'm beginning to think that this might be a problem on Vista's end.  Because I've had the OS drive on Ubuntu for as long as I've had Ubuntu, which means that it is being detected, but can't be mounted.  I can't think of any reason for this besides Vista messing up.  A friend suggested UAC could be the problem.  Thoughts?

---

### Post by jerome1232 on 2008-10-07
> **ucal said:**
> That would make sense considering that it is an NTFS partition, but dev/sda3 is already in the fstab.  

```
/dev/sda3       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I followed the instructions on that site, and that is how I found this.  Maybe I'm doing something wrong though.  I also used a script from that site which mounted sda2, but that doesn't include most of my windows partition.  Just system specific stuff I think.

That is an entry for a cdrom, not an ntfs drive..

change it to

```
/dev/sda3    /media/windows    ntfs-3g    defaults    0 0
```

---

### Post by ucal on 2008-10-08
Thanks to everyone.  Problem solved.

---

