---
title: "Swap file error 8.10"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by C-130 on 2009-03-06
Hi all. I ahve a 500GB had drive and 4GB of RAM. Tonight after loosing my operating system last Saturday 9which was Vista) I decided that since I had previous expereince and liked ubuntu I would install it, this has all been fine and dandy except for one thing, when i go to install I get to 15% on the installation and am greeted by the following:

The creation of swap space in partition #5 of SCSI2 (0,0,0) (sda) failed.

I have allowed a swap partition which eequates to double the amount of RAM my computer has and the file system has ranged from 32FAT to the standard linux one. I have used Guided install as well to no avail and tried this reinstall several times. At this minute my only avail is that ubuntu provides a basic operating system even if not installed. 

I would thank anyone for help in this matter.

---

### Post by taurus on 2009-03-06
How many primary partitions do you have on that harddrive?  For swap partition, the filesystem is _swap_, not fat32 or linux filesystem.

---

### Post by C-130 on 2009-03-06
I have one primary partition. I have it set up as follows:

New partition-Type of parititon Primary, 
New partition in MB- 491915 (the rest for swap space)
Location for new partition- beginning
Use as-Ext3 journaling file system
Mount Point- /

The Swap partition is set up only as swap and is allocated the remaining hard drive space. Its time of partition is Logical. 

If any help can be given form that then please do so.

---

### Post by guywithcable on 2009-03-06
Well if you have no (and I mean **NO**) important data on the drive at all, you could create a new partition table on the disk. This will make sure the disk is like new and may solve your problem. Boot into Ubuntu from the CD, go to System -> Administration ->Partition Editor. Select the drive you want to install onto, if it's not already selected, and under the Device menu, click Create Partition Table. After you finish, try installing again.

---

### Post by taurus on 2009-03-06
From Ubuntu LiveCD, open a terminal and run this command.  Post the output here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by C-130 on 2009-03-07
taurus thank you for this but unfortunately it does not offer an output, I type that instruction in and hit enter and then nothing. 

guywithcable the partitioner has not detected my hard drive. I know in install it detects my hard drive any help here?

---

### Post by linux_tech on 2009-03-07
-l is lowercase L

---

### Post by C-130 on 2009-03-07
> **linux_tech said:**
> -l is lowercase L

Thank you and here is what I get from the terminal:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda
ubuntu@ubuntu:~$ sudo fdisk - l

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 

This means nothing to me.

---

### Post by Hobgoblin on 2009-03-07
> **C-130 said:**
> 
guywithcable the partitioner has not detected my hard drive. I know in install it detects my hard drive any help here?

I think your drive was failing and has failed.

Try the install again, selecting the automatic partitioning option to use the whole drive.

If you know the make of the drive the manufacturers website will have diagnostic software for download which may confirm this.

---

### Post by C-130 on 2009-03-07
I have an hitachi hard drive.

---

### Post by C-130 on 2009-03-07
Hi all.

I have got ubuntu installed sadly I do not think it is installed over my entire hard drive. I ahve a 500GB drive and I think the install only has 7GB as my hard drive storage. Can anyone tell me how to confirm this?

---

### Post by taurus on 2009-03-07
Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by C-130 on 2009-03-07
The following is returned when I enter that into terminal:

colin@colin-desktop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
colin@colin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             425G  7.1G  397G   2% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.9M  1.7G   1% /dev
tmpfs                 1.7G  104K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             149G  4.3G  145G   3% /media/ADMIN'S IPO


Now that means very little to me. I have come from the world of widnows to ubuntu and this is unusual for myself.

---

### Post by taurus on 2009-03-07
> **C-130 said:**
> The following is returned when I enter that into terminal:

colin@colin-desktop:~$ **[COLOR="Red"]fdisk -l[/COLOR]**
Cannot open /dev/sda
Cannot open /dev/sdb
colin@colin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda6             425G  7.1G  397G   2% /[/COLOR]**
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.9M  1.7G   1% /dev
tmpfs                 1.7G  104K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             149G  4.3G  145G   3% /media/ADMIN'S IPO


Now that means very little to me. I have come from the world of widnows to ubuntu and this is unusual for myself.

For the first command, you need to include the sudo in front.

```
**[COLOR="Blue"]sudo[/COLOR]** fdisk -l
```

However, looks like you've assigned 425GB to / (root filesystem) and you are currently only using 7.1GB of it, 2%.

---

### Post by guywithcable on 2009-03-07
Considering the trouble you've had, your disk might be failing as suggested before. You can check your disk for bad blocks by using this from a live CD. Boot the Live CD again and put this in a terminal:

```
fsck -fc /dev/sda6
```

It might not be /dev/sda6 from the live CD, so try tinkering with the letter "a" in sda6 (like sdb6 for example) until you get it checking your disk.

This will take a long time. My 500 GB disk takes about 30 to 60 minutes to check.

---

### Post by C-130 on 2009-03-07
I ahve managed to install ubuntu. Now my problem lies with the file system. I shall perform the checks suggested. And once again want to thank you all for the wondrous help offered here.

---

