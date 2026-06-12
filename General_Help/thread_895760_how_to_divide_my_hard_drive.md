---
title: "how to divide my hard drive?"
date: 2008-08-20
forum: General Help
---

### Post by kboy on 2008-08-20
Hi,
i've recently bought a new 500GB hard drive.
I've divided it in the following manner:

25 GB - root partition (ext3)
40 GB - home partition (ext3)
4 GB - swap partition
150 GB - for videos and stuff... (ext3)
150 GB - for music and stuff... (ext3)
96 GB - other (ext3)

all of the partition are ext3, the problem is i don't have permission to write to them.
before this install i had my old drive partitioned with NTFS partitions, and i had no problem writing.

how can i solve this????

---

### Post by SuperSonic4 on 2008-08-20
did you do "gksudo gparted"?

it could be that your devices (in /media) are not mounted

---

### Post by LateNiteTV on 2008-08-20
why do u have a 4g swap partition? thats a bit overkill.

---

### Post by kboy on 2008-08-20
> did you do "gksudo gparted"?

what do you mean by that???

and i think my partitions are mounted, otherwise how could i have accessed them???


> why do u have a 4g swap partition? thats a bit overkill.

I heard you should do a swap partition twice the size my memory.

---

### Post by LateNiteTV on 2008-08-20
it may be a problem with having extended partitions. 
if i were u, i would only use:
/
swap
/usr
/home

leave the most room in /home and just add directories for your media instead of partitions. maybe that will fix your problem.

---

### Post by kboy on 2008-08-20
is there any other way to fix this????
i don't really wont to reinstall ubuntu

---

### Post by Elfy on 2008-08-20
First have they been added to fstab to mount automatically, it is probably best to do so - if you want to then we can, the permissions can be dealt with at the same time.

It's not a problem with haivng extended partitions.

If you have a need to hibernate then swap should equal RAM, but if not then I would only have a small swap with 2Gb RAM.


If you do run these commands in a terminal and post them

```
sudo fdisk -l
cat /etc/fstab
df -h
sudo blkid
```

Edit - that is a very large / partition do you intend on installing a lot of stuff :)

---

### Post by LateNiteTV on 2008-08-20
> **kboy said:**
> what do you mean by that???

and i think my partitions are mounted, otherwise how could i have accessed them???




**I heard you should do a swap partition twice the size my memory**.

that was back in the day when most computers had 128mb or less. you have 2g of ram... you shouldnt even need a swap partition.

---

### Post by kboy on 2008-08-20
**fdisk -l:**

```
fibo@my-ubuntu:~/Desktop$ sudo fdisk -l
[sudo] password for fibo:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9fd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+  83  Linux
/dev/sda2            3265        8486    41945715   83  Linux
/dev/sda3            8487        9008     4192965   82  Linux swap / Solaris
/dev/sda4            9009       60801   416027272+   5  Extended
/dev/sda5            9009       28589   157284351   83  Linux
/dev/sda6           28590       48170   157284351   83  Linux
/dev/sda7           48171       60801   101458476   83  Linux

```

[B]cat /etc/fstab :
[/B]
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ef03fa71-93bd-4ace-9a82-58e5d265b142 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=d3dd7efb-b1dc-443e-b22b-761caef24864 /home           ext3    defaults        0       2
# /dev/sda5
UUID=41f80306-0973-477f-b4c8-e84bfb27d516 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=dfdd17c8-7537-4fa5-80e0-b31031534326 /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=0ac765bb-5f2c-42e3-9f7c-2521d6d1de0d /media/sda7     ext3    defaults        0       2
# /dev/sda3
UUID=8a48656a-d9e9-4056-977f-631969d71642 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

**df -h**

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              25G  3.4G   20G  15% /
varrun               1014M   88K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   92K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-15-generic/volatile
/dev/sda2              40G  6.5G   31G  18% /home
/dev/sda5             148G  188M  140G   1% /media/sda5
/dev/sda6             148G  188M  140G   1% /media/sda6
/dev/sda7              96G  188M   91G   1% /media/sda7
/dev/scd0             3.5G  3.5G     0 100% /media/cdrom0

```

**sudo blklid :**

> /dev/sda1: UUID="ef03fa71-93bd-4ace-9a82-58e5d265b142" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="d3dd7efb-b1dc-443e-b22b-761caef24864" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="8a48656a-d9e9-4056-977f-631969d71642" 
/dev/sda5: UUID="41f80306-0973-477f-b4c8-e84bfb27d516" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="dfdd17c8-7537-4fa5-80e0-b31031534326" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="0ac765bb-5f2c-42e3-9f7c-2521d6d1de0d" SEC_TYPE="ext2" TYPE="ext3" 


and is there a way to resize the swap partition without reinstalling ubuntu??

---

### Post by bodhi.zazen on 2008-08-20
This is a "basic" permissions issue.

For linux native file systems you need to use chown and chmod to set ownership and permissions. This is a "one time" configuration.

[uhelp]community/FilePermissions[/uhelp]

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You partitions are located at /media/sda5 , /media/sda6 , and /media/sda7

```
sudo chown root.fibo /media/sda{5,6,7}
sudo chmod -R 770 /media/sda{5,6,7}
```

---

### Post by kboy on 2008-08-20
thanks allot!!

---

### Post by Elfy on 2008-08-20
Ok - just the permissions to do then, this should do it I think for the first - 

```
sudo chown -R <username>:<username> /media/sda5
```

Change username to yours and then repeat for each of sda6 and 7, should do it. Might need to chmod though.

---

### Post by mikjp on 2008-08-20
> **kboy said:**
> Hi,
25 GB - root partition (ext3)

I suppose you'll never need that much in / unless you are running a web server. Usually 5-10 is enough for me :-)

More interesting than the exact partitions for multimedia is, in my opinion, the place where you mount them. 

mikko

---

