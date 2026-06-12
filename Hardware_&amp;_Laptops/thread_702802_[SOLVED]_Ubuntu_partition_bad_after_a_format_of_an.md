---
title: "[SOLVED] Ubuntu partition bad after a format of another partiton"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by carlinuxlearner on 2008-02-20
Well first of all, I'm not even sure this thread should be in this section, so feel free to move it.

And please ignore the "Title", I had not investigated enough when I made this thread, and I thought something really bad had happend, So I apologize for not doing my "homework" before posting.


I had Ubuntu installed, my hard drive was partitioned already so I could install another Linux distro, while installing it asked me if I wanted to format the partition that was going to be used as "/" I said yes. 

Although Ubuntu is still there and every things fine, on of my partitions is now NOT "clean" according to "fsck", and it's the one that was formated, so now Ubuntu complains about it every time I boot.

I have had this happen before, but WHY did it mess it up when all I did was reformat??

Here is the log file.

checkfs

Log of fsck -C -R -A -a 
Wed Feb 20 18:37:52 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda2: clean, 17899/6406144 files, 3840484/12799788 blocks (check in 3 mounts)
fsck.ext3: Unable to resolve 'UUID=ccabf627-71c4-498f-9ae5-f5241e26387c'

/dev/sda7: clean, 11/2562240 files, 124467/5120710 blocks
/dev/sda8: clean, 11/2562240 files, 124467/5120710 blocks
/dev/sda9: clean, 11/2752512 files, 130435/5496230 blocks
/dev/sda3: clean, 129075/6406144 files, 1167171/12799788 blocks
fsck died with exit status 8

Wed Feb 20 18:37:54 2008
----------------

checkroot

Log of fsck -C -a -t ext3 /dev/sda5 
Wed Feb 20 18:37:52 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda5: clean, 16101/7176192 files, 519821/14335996 blocks

Wed Feb 20 18:37:52 2008
----------------

So is it "safe" for me to reformat it with "gparted"? And will that fix it?

C@RL

---

### Post by DoctorMO on 2008-02-20
did you partition it and forget to format the disk? after repartitioning you should format disks so the old data doesn't leak into the new partition.

---

### Post by carlinuxlearner on 2008-02-20
When I first partitioned it I believe it formated it (seeing as it had me choose what file system was to go on each partition), and it's a bran-new HD.
So what I did was.

1. Partitioned HD. (about 6 different partitions for all the distros I'm going to try out)
2. installed Ubuntu.
3. Installed Debian Etch. (it didn't see my network card or SATA DVD-ROM)
4. Installed Etch again (this is when I reformatted the partition)
5. Booted into Ubuntu (stops in the middle of booting to tell me a partition didn't pass the test)
6. I press CTRL+D and continue the boot process. (and now here I am on the forums)

C@RL

---

### Post by farsight on 2008-02-20
im no expert so laugh if i'm wrong but would it have anything to defragmenting? I know when you create a dual boot using Vista to create and manage partitions it recommends defragmenting before continuing. Though if it has formatted i'm not certain this could happen.

---

### Post by carlinuxlearner on 2008-02-20
Well I won't laugh, but your wrong. 
You see Ubuntu uses the "ext3" file system, which resists fragmentation. I say resists because under normal conditions it will NOT become fragmented at ALL, however if your hard drive is nearly full, it can become fragmented.

So defragmenting is for Windows only. (because it uses a file system that gets fragmented quite frequently)

All I want to know is, if I reformat it with gparted will it fix the problem? Or will it still fail the fsck test?

C@RL

---

### Post by DoctorMO on 2008-02-21
If you reformat it should fix it since the data that fsck is checking will be reset.

---

### Post by carlinuxlearner on 2008-02-21
Well I reformatted it with Gparted and it still complains while booting.

C@RL

---

### Post by Yellow Pasque on 2008-02-21
What is it complaining about, the UUID? Do you mean this line?:
> fsck.ext3: Unable to resolve 'UUID=ccabf627-71c4-498f-9ae5-f5241e26387c'

Ok, run these commands:
```
sudo fdisk -l
cd /dev/disk/by-uuid; ls -l
cat /etc/fstab
```

---

### Post by carlinuxlearner on 2008-02-23
Well I ran all that and it didn't do any thing. Here's the output of those commands:

```
carl@carl-desktop:~$ sudo fdisk -l
[sudo] password for carl:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1a9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         127     1020096   82  Linux swap / Solaris
/dev/sda2             128        6501    51199155   83  Linux
/dev/sda3            6502       12875    51199155   83  Linux
/dev/sda4           12876       30401   140777595    5  Extended
/dev/sda5   *       12876       20014    57343986   83  Linux
/dev/sda6           20015       24792    38379253+  83  Linux
/dev/sda7           24793       30401    45054261   83  Linux
carl@carl-desktop:~$ cd /dev/disk/by-uuid; ls -l
total 0
lrwxrwxrwx 1 root root 10 2008-02-23 19:18 0d7a6179-5840-4a13-9271-336fe9873f09 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-02-23 19:18 22485fe5-70a0-4465-8a93-a5d072d2bae7 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-02-23 19:18 88b9984b-747b-4493-9a2e-f71be226208c -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-02-23 19:18 d845ea5b-a491-44ec-9c4e-4af65f73b3d8 -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-02-23 19:18 dc94f570-ae0f-48d7-abfd-8b6bb28787a4 -> ../../sda2
carl@carl-desktop:/dev/disk/by-uuid$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=88b9984b-747b-4493-9a2e-f71be226208c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=dc94f570-ae0f-48d7-abfd-8b6bb28787a4 /home           ext3    defaults        0       2
# /dev/sda6
UUID=ccabf627-71c4-498f-9ae5-f5241e26387c /media/other1   ext3    defaults        0       2
# /dev/sda7
UUID=5fd0f853-cb4f-42b8-83b7-7ce98a413146 /media/other2   ext3    defaults        0       2
# /dev/sda8
UUID=a282bd54-81d3-4f49-9ad4-456a38abfa29 /media/other3   ext3    defaults        0       2
# /dev/sda9
UUID=936ff445-e741-4ea2-95a8-ae74903e88fc /media/other4   ext3    defaults        0       2
# /dev/sda3
UUID=22485fe5-70a0-4465-8a93-a5d072d2bae7 /usr            ext3    defaults        0       2
# /dev/sda1
UUID=2956d9be-d321-4e03-b6bc-fd1c8f770dec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
carl@carl-desktop:/dev/disk/by-uuid$ 

```

C@RL

Sorry it took so long to reply, I was downloading a large file.

---

### Post by Yellow Pasque on 2008-02-23
Yeah, you have an incorrect UUID for /dev/sda6/

This is the UUID in the directory listing:
```
0d7a6179-5840-4a13-9271-336fe9873f09 -> ../../sda6
```

This is what your /etc/fstab is looking for:
```
# /dev/sda6
UUID=ccabf627-71c4-498f-9ae5-f5241e26387c
```

So, sudo gedit /etc/fstab and correct that value.

---

### Post by carlinuxlearner on 2008-02-23
Alright! Thanks, it's all working now.

C@RL

---

