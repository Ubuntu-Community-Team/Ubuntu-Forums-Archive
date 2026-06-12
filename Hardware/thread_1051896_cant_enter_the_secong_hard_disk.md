---
title: "cant enter the secong hard disk"
date: 2009-01-27
forum: Hardware
---

### Post by nouraldin on 2009-01-27
hi all 
couple days ago i installed Ubuntu on my PC before that i had xp ,
and in win xp i had drivers "d" and "c" ,
in the installation progress of Ubuntu i chose to install it on the drive "c" ,
since on drive "d" i have many data like films etc...
and now i cant enter drive d ,and i don't want to use the force element and lose all the data on it .
is there any another way to enter drive "d" without lose any data that on it ?
thanks for the helpers.

---

### Post by vanadium on 2009-01-27
I am afraid you only have one drive with two partitions, not two drives like Windows was telling you.

> n the installation progress of Ubuntu i chose to install it on the drive "c" 

Ubuntu does not know about drive c or drive d. If you let it use the entire drive, then it will wipe and format that drive. If there are two partitions on the drive, both partitions will be wiped.

This is a bad scenario which I assume has happened. However, I might be wrong (you might have two disks or done things a little differently than I understand). To make sure, show us the current partitioning and use of your drives by posting the output of the commands

```

sudo fdisk -l
mount

```

If your d partition is still there, it will show up and we will be able to tell you where to look.

---

### Post by nouraldin on 2009-01-27
OK thanks 
here is what i get :
 "
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x866f866f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order"

---

### Post by vanadium on 2009-01-27
Actually you *do* have two disks, although the partition table of your second disk is very messy, not to say corrupt. If I were you, I would try to copy all data elsewhere and repartition/reformat that disk.

I am not sure wether that second disk is supposed to show up under "Places", where, normally, you could mount and get access to it by clicking.

Anyway, you could try whether that partition is accessible with the following commands:

[code]
cd
mkdir temp
sudo mount /dev/sdb1 temp
[code]
If you do not have any output (which I doubt strongly), you should see the contents of the ntfs partition navigating into temp. You would better copy the needed data to a safe location then.

Else, copy/paste the output (error message) here along with the command you gave.

---

### Post by nouraldin on 2009-01-27
ok that what i got 

" mount: special device /dev/sdb1 does not exist "

if u have any other ideas how to get open the driver i will be happy to hear ,

and if not. simply i will format it without saving the data in it .
because just the movies in it i didnt backup so its ok 

:D

---

### Post by nouraldin on 2009-01-27
i have write in the terminal :
"sudo mkfs -t ext3 /dev/sdb"

and it work partly ,formating the second hard disk i have ,
but,
first of all i have lost 13 GB from the disk space (that originally is 232 GB).

secondly i tried to move to it some data but it gave me an error .

so i will be glad for any suggestion. 
regards nouraldin.

---

### Post by nouraldin on 2009-01-28
help

---

### Post by vanadium on 2009-01-28
You should post both the command and the output so we can be sure an error message is not due to typing errors. If you entered the mount command as suggested, then it would mean that the partition cannot be found anymore, despite fdisk still reporting something. This would indeed confirm major corruption of the drive's partition table.

Anyway, formatting aside, tedious recovery procedures would have been your only option. You probably did the best thing: a plain reformat.

You now have formatted the disk in ext3. However, you wiped any partition table the way you did it. This is not a problem in its own right, though. It only means you cannot create partitions on that drive: it only holds the current file system.

It is normal that you "lost" 13 GB: about 5% of the file system is reserved for root operations with ext2/ext3.

In summary to the above: essentially you are all set.Your next step is to mount and use the partition. I am giving command line instructions for brevity.

1) Make mount point
```

sudo mkdir /mnt/sdb

```

2) Add a line to /etc/fstab for the drive. We will backup your existing fstab first.

```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
[code]

Your configuration file /etc/fstab should now open in the editor gedit. Add following line to the end, then save the file.

[code]
/dev/sdb /mnt/sdb ext3 defaults 0 2

```

3) Check you modified fstab properly and mount the drive.

```

sudo mount -a

```

You should not have any output. If you do, stop here and post the output, along with the output of "cat /etc/fstab". It means there is an error with your /etc/fstab and we need to correct that before going on.

If there is no error, your drive will be mounted. However, you will not be able to access it yet. We need to give you permissiosn for that.

4) Create a directory on the new drive and give ownership to you as a regular user.

```

sudo mkdir /mnt/sdb/data
sudo chown $USER:$USER /mnt/sdb/data

```

You can type $USER as is. This will be replaced by your own user name. If you want to do this for another user, substitute his login instead of $USER.

5) For easy access from within your home directory, create a symbolic link to it

```

ln -s /mnt/sdb/data data

```

Now, you should find a directory "data" inside your home directory. If you navigate into it, it will be empty, but you should be able to store data into it. Obviously, you can rename the link from "data" to anything you like.

---

### Post by nouraldin on 2009-01-28
ok i hope u got other ideas becose that way didn't work i copied and past evrey step as u told me .
but no "data" drive had been added ,
by the way i restarted and it gave me like a sentence or tow of error but it resummed the booting  ,
and i checked for the new "data" and nothing appears there  .
can u give me an explanation for every step i make in the commands u posted to me

---

### Post by vanadium on 2009-01-28
I did. If you had copied commands and output here, I could have seen where it went wrong.

---

### Post by phenacomy on 2009-03-05
I orginally loaded Intrepid on a 8GB HD as a single master. I then added a 2nd HD (60GB) & now I've got the 8GB HD booting Intrepid & a 60GB HD I'm using to store streaming media ---- sudo disk -l    SHOWS:

Disk /dev/sda: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x000c85f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7753    58612648+  83  Linux

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9a8b9a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         978     7855753+  83  Linux
/dev/sdb2             979        1027      393592+   5  Extended
/dev/sdb5             979        1027      393561   82  Linux swap/Solaris

however ----- sudo nano /etc/fstab    SHOWS:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e7fb3b3d-0013-475b-ad5b-09a8ce9b7410 /               ext3    relatime,erro$
# /dev/sda5
UUID=027b1d67-5307-4c18-8518-62427ee12795 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I'd like to edit fstab to mount the 60GB automatically but the naming has got me confused. WTF is up with fstab showing the 8GB as sda1 & not listing the 60GB at all, while disk -l shows the 60GB as sda1 & the 8GB as sdb? If I were to rewrite fstab do I have to include the UUIDs? If I rewrite fstab I risk losing the partitions correct? How do I fix this?

Thanks

---

