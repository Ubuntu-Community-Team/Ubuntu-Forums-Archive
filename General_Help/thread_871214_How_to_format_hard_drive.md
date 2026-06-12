---
title: "How to format hard drive?"
date: 2008-07-26
forum: General Help
---

### Post by gretarsson on 2008-07-26
Hi I have 2 hard disk 1. 250GB (A) and 1. 500GB (B).
I have ubuntu on both disk but I start up on disk A and like to format disk B. Like it is to day I can not cope file into disk B which I like to use as extra disk, I like to do this with terminal but to know how.... 
Thanks.

---

### Post by rob1101 on 2008-07-26
im not really sure what your question is? 

I partition disks a lot and I like to boot up into [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php") (small live linux distro) it gives a nice GUI and makes things really easy.

---

### Post by A. J. Rimmer on 2008-07-26
You could install Gparted using Synaptic, and that will let you format and partition drives.

(Be very careful that you do not format the wrong drive!)

You could also go to gparted.sourceforge.net and download the iso for Gparted and make it into a live CD.  You would then boot into the live CD and use Gparted to do the formatting and partitioning.

---

### Post by gretarsson on 2008-07-26
> **A. J. Rimmer said:**
> You could install Gparted using Synaptic, and that will let you format and partition drives.

(Be very careful that you do not format the wrong drive!)

You could also go to gparted.sourceforge.net and download the iso for Gparted and make it into a live CD.  You would then boot into the live CD and use Gparted to do the formatting and partitioning.

Hi I tried to use gparted but it is easy to see what disk I haft to format but I have try every thing in that program, format and make new label but it is still same I can not cope files into that disk.

---

### Post by PeterBBB on 2008-07-26
The partition sdb2 is already formatted. You just need to mount it.

[http://help.ubuntu.com/community/InstallingANewHardDrive#Create a Mount Point]("http://help.ubuntu.com/community/InstallingANewHardDrive#Create a Mount Point")


PB.

---

### Post by richardjennings on 2008-07-26
the disk is already mounted at /media/disk/  as per the screenshot. I think the problem might be that you do not have permission to write to the disk. Can you either try:

```
sudo nautilus /media/disk
```
this will open nautilus with root privilidges

then try drag and drop a file

or post your /etc/fstab so we can see how the drive is being mounted

```
cat /etc/fstab
```

---

### Post by richardjennings on 2008-07-26
just as a note:

if you wish to use the free space on the 2nd drive that the Ubuntu install is not using, you might find it easier, more logical, to resize the ubuntu partition /dev/sdb1 to around 20gigs or so, then create a new ext3 partition with the remaining space. I think this is what you want to do. If you do NOT want the 2nd ubuntu install, delete all the partitions & make a new ext3 partition using the whole drive. If you DO want to keep the 2nd ubuntu install, make a swap partition after sdb1 then use the rest of the space as a new ext3 partition. Make all the partitions primary, extended is not neccessery in this situation (allows for more than 4 partitions).

---

### Post by gretarsson on 2008-07-26
> **richardjennings said:**
> the disk is already mounted at /media/disk/  as per the screenshot. I think the problem might be that you do not have permission to write to the disk. Can you either try:

```
sudo nautilus /media/disk
```
this will open nautilus with root privilidges

then try drag and drop a file

or post your /etc/fstab so we can see how the drive is being mounted

```
cat /etc/fstab
```

Hi and thanks
But if I try sudo nautilus /media/disk I got this 

seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:10911): WARNING **: Unable to add monitor: Operation not supported
-------------------------
and I still can not drag and drop file on that disk (this is extra hdd not prime hdd)

---

### Post by richardjennings on 2008-07-26
```
sudo mkdir /media/disk/test/
```

any errors? if not, there should be a directory called test on the 2nd disks root partition.

```
sudo chown yourusername /media/disk/test
```

you should now be able to write to the folder test on the 2nd harddrive.

to test make a new directory in the test folder without root permission,

```
mkdir /media/disk/test/ok/
```

```
cd /media/disk/test/ok/
```

did that all work?

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> ```
sudo mkdir /media/disk/test/
```

any errors? if not, there should be a directory called test on the 2nd disks root partition.

```
sudo chown yourusername /media/disk/test
```

you should now be able to write to the folder test on the 2nd harddrive.

to test make a new directory in the test folder without root permission,

```
mkdir /media/disk/test/ok/
```

```
cd /media/disk/test/ok/
```

did that all work?

Hi and THANKS for the help but when I do this well see here I cope and paste it from my terminal....

jon@jon:~$ sudo mkdir /media/disk/test/
[sudo] password for jon: 
jon@jon:~$ sudo mkdir /media/disk/test/
mkdir: cannot create directory `/media/disk/test/': File exists
jon@jon:~$ sudo chown jon /media/disk/test
jon@jon:~$ mkdir /media/disk/test/ok/
mkdir: cannot create directory `/media/disk/test/ok/': No space left on device
jon@jon:~$ 
does this tell you some thing about what is wrong...

---

### Post by Elfy on 2008-07-27
can you post the fstab and the other command

```
cat /etc/fstab
df -h
```

---

### Post by gretarsson on 2008-07-27
> **forestpixie said:**
> can you post the fstab and the other command

```
cat /etc/fstab
df -h
```

Hi and Thanks for the help, here are my display from my terminal...

jon@jon:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=32a774a8-28be-421d-9803-40809f820538 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3e5fc97f-2d82-4235-8018-8298456da704 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jon@jon:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             223G  178G   35G  84% /
varrun                1.5G  232K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   68K  1.5G   1% /dev
devshm                1.5G  868K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      223G  178G   35G  84% /home/jon/.gvfs
/dev/sdc1             223G  212G     0 100% /media/disk
jon@jon:~$

---

### Post by Elfy on 2008-07-27
We can easily enough place the drive in fstab so that it will mount on boot, what name do you want the drive to mount as?

Can you also provide output of

```
sudo blkid
```

---

### Post by gretarsson on 2008-07-27
> **forestpixie said:**
> We can easily enough place the drive in fstab so that it will mount on boot, what name do you want the drive to mount as?

Can you also provide output of

```
sudo blkid
```
Hi again
here is paste from my terminal 

jon@jon:~$ sudo blkid
[sudo] password for jon: 
/dev/sda5: TYPE="swap" UUID="3e5fc97f-2d82-4235-8018-8298456da704" 
/dev/sdb1: UUID="5690142B901413D9" TYPE="ntfs" 
/dev/sdc1: UUID="4ab63b8b-6f90-417f-b85a-4a64afa007ff" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="d36fb368-f962-4b05-aab0-b769754f70ef" 
/dev/sda1: UUID="32a774a8-28be-421d-9803-40809f820538" TYPE="ext3" 

but to be sure we are fixing the right disk I have 2 disk 1. 250GB with os ubuntu on it that disk is fine but disk 2. 500GB is new had Mvista on it before that disk I can see but can not paste any file on it.

---

### Post by ezsit on 2008-07-27
Only proceed if you wish to format the partition in question. This will delete all data! Make sure you are working with the correct partition before going any further.

OK, if you have not managed to get this done yet, try the following (all bolded commands should be typed at the terminal):

Step one, unmount the partition:
**sudo umount /dev/sdb1**

Step two, deactivate the swap partition on the physical drive:
**sudo swapoff /dev/sdb5**

Step three, format the partition:
**sudo mkfs.ext3 /dev/sdb1**

Step four, create a mountpoint:
**sudo mkdir /mnt/new_disk**

Step five, mount the partition:
**sudo mount /dev/sdb1 /mnt/new_disk**

Step six, change ownership of the mountpoint:
**sudo chown yourusername:yourusername /mnt/new_disk**

At this point you should have an empty partition, formatted as ext3, mounted at /mnt/new_disk that you as the user can copy files to and delete files from.

If you would like this partition mounted at each boot you will need to add a line to your fstab, something like:

/dev/sdb1 /mnt/new_disk ext3 defaults,rw 0 0

I hope this helps. Let us know.

---

### Post by Elfy on 2008-07-27
LEts double check then - I can see that you have 3 hdds

sda - appears to have a linux install (which I assume is ubuntu) and a swap

sdb - appears to have win format partition

sdc - appears to have a linux install and a swap

Are you using both swaps for a reason?

I am assuming you wish to mount and have access to the drive formatted as ntfs - if that is the case and you do not want it to be a linux partition you can install a tool to use the intrenal drive.

If you want to make it linux it will need reformatting.

If you only have 2 drives please provide

```
sudo fdisk -l
```

---

### Post by PeterBBB on 2008-07-27
> **PeterBBB said:**
> The partition sdb2 is already formatted. You just need to mount it.

PB.

My typo, sorry. That should have been sdb1. From your image, sdb2 is an extended (container) partition. Should'nt try to mount that.

We need to see the output of 

sudo fdisk -l

as a third disk (sdc) seems to have appeared!

---

### Post by gretarsson on 2008-07-27
> **forestpixie said:**
> LEts double check then - I can see that you have 3 hdds

sda - appears to have a linux install (which I assume is ubuntu) and a swap

sdb - appears to have win format partition

sdc - appears to have a linux install and a swap

Are you using both swaps for a reason?

I am assuming you wish to mount and have access to the drive formatted as ntfs - if that is the case and you do not want it to be a linux partition you can install a tool to use the intrenal drive.

If you want to make it linux it will need reformatting.

If you only have 2 drives please provide

```
sudo fdisk -l
```

sorry my mistake
I was in my computer when I was writing to you, it is my son computer which have disable disk and he have 2 disk mine have 3 disk so I haft to do this again and send you the info...sorry

---

### Post by Elfy on 2008-07-27
He he he - makes all the differnce :) Once you have the information you can, make a suitable folder for it to mount to , edit fstab and chmod as required

Make folder - choose name to suit

```
sudo mkdir /media/[COLOR="#ff0000"]name[/COLOR]
```

Edit fstab

```
gksudo gedit /etc/fstab
```

Add this to fstab - use previous blkid command to retrieve correct UUID

> #dev#sdb
UUID=*getnumberfromblkid* /media/[COLOR="Red"]name[/COLOR] ext3 relatime 0 2

```
sudo chown user.user /media/[COLOR="#ff0000"]name[/COLOR]
sudo chmod 770 /media/[COLOR="#ff0000"]name[/COLOR]
```

Whatever you use as [COLOR="#ff0000"]name[/COLOR] should be the same in all instances

Check that it has mounted properly with 

```
sudo mount -a
```

---

### Post by richardjennings on 2008-07-27
gretarsson have you changed any of the partitions since the screen shots you posted? The screen shot shows the partition /dev/sdb1 mounted at /media/disk with over 400gb of free space.

---

### Post by Elfy on 2008-07-27
> **richardjennings said:**
> gretarsson have you changed any of the partitions since the screen shots you posted? The screen shot shows the partition /dev/sdb1 mounted at /media/disk with over 400gb of free space.

different pc

---

### Post by gretarsson on 2008-07-27
> **forestpixie said:**
> He he he - makes all the differnce :) Once you have the information you can, make a suitable folder for it to mount to , edit fstab and chmod as required

Make folder - choose name to suit

```
sudo mkdir /media/[COLOR="#ff0000"]name[/COLOR]
```

Edit fstab

```
gksudo gedit /etc/fstab
```

Add this to fstab



```
sudo chown user.user /media/[COLOR="#ff0000"]name[/COLOR]
sudo chmod 770 /media/[COLOR="#ff0000"]name[/COLOR]
```

Whatever you use as [COLOR="#ff0000"]name[/COLOR] should be the same in all instances

Check that it has mounted properly with 

```
sudo mount -a
```
Hi again
I can not see 500GB disk on that list but he come up on file map (places)
that disk I need to fix
here are the right list from my son pc
code:
bjarki@bjarki:~$ sudo blkid
[sudo] password for bjarki: 
/dev/sda1: UUID="1b54e307-65a8-4b8d-8b68-a6100071e046" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="898d45f4-e0d5-463d-9fc9-70377542f6bd" 
/dev/sdb1: UUID="67a154f1-01ab-4c12-9256-0c42974cb372" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="ea9d297b-a480-4237-afe6-9473764dfba0" 
bjarki@bjarki:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b54e307-65a8-4b8d-8b68-a6100071e046 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=898d45f4-e0d5-463d-9fc9-70377542f6bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
bjarki@bjarki:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G   19G  116G  14% /
varrun                1.5G  224K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-20-generic/volatile
gvfs-fuse-daemon      142G   19G  116G  14% /home/bjarki/.gvfs
bjarki@bjarki:~$ fdisk -l
bjarki@bjarki:~$ 
bjarki@bjarki:~$ fdisk -h
fdisk: invalid option -- h

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
bjarki@bjarki:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-20-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bjarki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bjarki)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by gretarsson on 2008-07-27
> **gretarsson said:**
> Hi again
I can not see 500GB disk on that list but he come up on file map (places)
that disk I need to fix
here are the right list from my son pc
code:
bjarki@bjarki:~$ sudo blkid
[sudo] password for bjarki: 
/dev/sda1: UUID="1b54e307-65a8-4b8d-8b68-a6100071e046" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="898d45f4-e0d5-463d-9fc9-70377542f6bd" 
/dev/sdb1: UUID="67a154f1-01ab-4c12-9256-0c42974cb372" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="ea9d297b-a480-4237-afe6-9473764dfba0" 
bjarki@bjarki:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b54e307-65a8-4b8d-8b68-a6100071e046 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=898d45f4-e0d5-463d-9fc9-70377542f6bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
bjarki@bjarki:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G   19G  116G  14% /
varrun                1.5G  224K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   44M  1.5G   3% /lib/modules/2.6.24-20-generic/volatile
gvfs-fuse-daemon      142G   19G  116G  14% /home/bjarki/.gvfs
bjarki@bjarki:~$ fdisk -l
bjarki@bjarki:~$ 
bjarki@bjarki:~$ fdisk -h
fdisk: invalid option -- h

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
bjarki@bjarki:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-20-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bjarki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bjarki)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

I tried to do this but I not sure if it works

bjarki@bjarki:~$ sudo mkdir /media/auka
bjarki@bjarki:~$ gksudo gedit /etc/fstab
bjarki@bjarki:~$ sudo chown user.user /media/name
chown: invalid user: `user.user'
bjarki@bjarki:~$ sudo chown user.user /media/name
chown: invalid user: `user.user'
bjarki@bjarki:~$ sudo chown user.user /media/auka
chown: invalid user: `user.user'
bjarki@bjarki:~$ sudo chmod 770 /media/auka
bjarki@bjarki:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/getnumberfromblkid does not exist
bjarki@bjarki:~$ 
file name is auka. (it mean extra)
-------------------------------------------
Here are me list from fstab
-------------------------------------------
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b54e307-65a8-4b8d-8b68-a6100071e046 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=898d45f4-e0d5-463d-9fc9-70377542f6bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#dev#sdb
UUID=getnumberfromblkid /media/auka ext3 relatime 0 2

---

### Post by armandh on 2008-07-27
I found that when attempting to add dual boot HH-8.04 on my wife's vista laptop I had to use the vista partition utility, as gparted, partition magic, and several others would not work.

after reducing the vista partition the "select unused space" option appeared in the HH install.

so the question is how was it partitioned/formatted?

---

### Post by richardjennings on 2008-07-27
Are you on the correct pc now gretarsson?

can you post 

```
df
```

&

```
sudo fdisk -l
```

&

```
sudo fschk /dev/sdb1
```

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> Are you on the correct pc now gretarsson?

can you post 

```
df
```

&

```
sudo fdisk -l
```

&

```
sudo fschk /dev/sdb1
```

Hi again here are the list
------------------------------------
bjarki@bjarki:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            148721272  19739672 121486476  14% /
varrun                 1548728       224   1548504   1% /var/run
varlock                1548728         0   1548728   0% /var/lock
udev                   1548728        60   1548668   1% /dev
devshm                 1548728        12   1548716   1% /dev/shm
lrm                    1548728     44968   1503760   3% /lib/modules/2.6.24-20-generic/volatile
gvfs-fuse-daemon     148721272  19739672 121486476  14% /home/bjarki/.gvfs
/dev/sdb1            475539124   2333632 449239728   1% /media/disk
bjarki@bjarki:~$ sudo fdisk -l
[sudo] password for bjarki: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00005e8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59672   479315308+  83  Linux
/dev/sdb2           59673       60801     9068692+   5  Extended
/dev/sdb5           59673       60801     9068661   82  Linux swap / Solaris
bjarki@bjarki:~$ sudo fschk /dev/sdb1
sudo: fschk: command not found
bjarki@bjarki:~$

---

### Post by gretarsson on 2008-07-27
> **armandh said:**
> I found that when attempting to add dual boot HH-8.04 on my wife's vista laptop I had to use the vista partition utility, as gparted, partition magic, and several others would not work.

after reducing the vista partition the "select unused space" option appeared in the HH install.

so the question is how was it partitioned/formatted?

Hi I but in ubuntu install disk and lit it install ubuntu on that extra disk with out karnel boot so it will not mess out me start up and that disk is ext3 now

---

### Post by richardjennings on 2008-07-27
ok so it is definately sdb1, and is definately mounted, and definately has free space.

im sorry i spelt the command wrongly,

can you run this:

```
sudo fsck /dev/sdb1
```

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> ok so it is definately sdb1, and is definately mounted, and definately has free space.

im sorry i spelt the command wrongly,

can you run this:

```
sudo fsck /dev/sdb1
```

Here is my terminal out print
-----------------------------------

bjarki@bjarki:~$ sudo fsck /dev/sdb1
[sudo] password for bjarki: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb1: recovering journal
/dev/sdb1: clean, 108035/29958144 files, 1527454/119828827 blocks
bjarki@bjarki:~$

---

### Post by gretarsson on 2008-07-27
> **gretarsson said:**
> Here is my terminal out print
-----------------------------------

bjarki@bjarki:~$ sudo fsck /dev/sdb1
[sudo] password for bjarki: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb1: recovering journal
/dev/sdb1: clean, 108035/29958144 files, 1527454/119828827 blocks
bjarki@bjarki:~$
----------------------------------------------
Is sdb1 my 500GB disk and sdb2 my 250GB, sdb2 is ok I put up ubuntu on both disk but I need to format 500GB disk

/dev/sdb1 1 59672 479315308+ 83 Linux
/dev/sdb2 59673 60801 9068692+ 5 Extended
----------------------------------------------
I but in ubuntu install disk and lit it install ubuntu on that extra disk with out karnel boot so it will not mess out me start up and that disk is ext3 now

---

### Post by richardjennings on 2008-07-27
so you DO want to delete the 2nd Ubuntu install & use the whole disk????


otherwise:

```
sudo chown yourusername.yourusername /media/disk
```

```
sudo chmod 770 /media/disk
```

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> so you DO want to delete the 2nd Ubuntu install & use the whole disk????


otherwise:

```
sudo chown yourusername.yourusername /media/disk
```

```
sudo chmod 770 /media/disk
```
yes I like to have that disk as extra disk for photos and media files
my 250GB disk is the main disk with ubuntu on it but I put in ubuntu install disk and lit it install ubuntu on that extra disk with out karnel boot so it will not mess out me start up and that disk is ext3, do you think I haft to delete what I put in to my fstab file before

---

### Post by richardjennings on 2008-07-27
sdb1 is definately the 2nd ubuntu install, i.e not the one you type the commands into. If you want to delete it and use the whole space for media files:

unmount the 2nd disk

```
sudo umount /media/disk
```

make sure you are not using the swapspace

```
sudo swapoff /dev/sdb5
```

open up gparted

goto the harddisk sdb

double and tripple check that you DO want to delete the ubuntu install... 

delete all the partitions

click apply

you should now have a blank disk

make a new primary ext3 partition using all the space

click apply

you should now have the whole of sdb as free space

type ```
mount
```

and the drive should be mounted, ready to use.

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> sdb1 is definately the 2nd ubuntu install, i.e not the one you type the commands into. If you want to delete it and use the whole space for media files:

unmount the 2nd disk

```
sudo umount /media/disk
```

make sure you are not using the swapspace

```
sudo swapoff /dev/sdb5
```

open up gparted

goto the harddisk sdb

double and tripple check that you DO want to delete the ubuntu install... 

delete all the partitions

click apply

you should now have a blank disk

make a new primary ext3 partition using all the space

click apply

you should now have the whole of sdb as free space

type ```
mount
```

and the drive should be mounted, ready to use.

--------------------------------------------------------
it say:

bjarki@bjarki:~$ sudo umount /media/disk
[sudo] password for bjarki: 
bjarki@bjarki:~$ sudo swapoff /dev/sdb5
swapoff: /dev/sdb5: Invalid argument
bjarki@bjarki:~$

---

### Post by gretarsson on 2008-07-27
> **gretarsson said:**
> --------------------------------------------------------
it say:

bjarki@bjarki:~$ sudo umount /media/disk
[sudo] password for bjarki: 
bjarki@bjarki:~$ sudo swapoff /dev/sdb5
swapoff: /dev/sdb5: Invalid argument
bjarki@bjarki:~$

here is my out print from terminal
---------------------------------------
bjarki@bjarki:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-20-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bjarki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bjarki)
bjarki@bjarki:~$
---------------------------------------------------------
but now my File browser can not see that disk

---

### Post by richardjennings on 2008-07-27
that means /dev/sdb5 is not being used for as swap space, all clear to launch gparted and delete all partitions on sdb.

edit: The fstab entry in incorrect!!

---

### Post by richardjennings on 2008-07-27
did you create the new partition?

```
sudo fdisk -l
``` should list the partition if you have.

---

### Post by richardjennings on 2008-07-27
# /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b54e307-65a8-4b8d-8b68-a6100071e046 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=898d45f4-e0d5-463d-9fc9-70377542f6bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#dev#sdb
UUID=getnumberfromblkid /media/auka ext3 relatime 0 2



this line

```
UUID=getnumberfromblkid /media/auka ext3 relatime 0 2
```

shouldnt be in your /etc/fstab

delete it

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> # /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b54e307-65a8-4b8d-8b68-a6100071e046 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=898d45f4-e0d5-463d-9fc9-70377542f6bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#dev#sdb
UUID=getnumberfromblkid /media/auka ext3 relatime 0 2



this line

```
UUID=getnumberfromblkid /media/auka ext3 relatime 0 2
```

shouldnt be in your /etc/fstab

delete it
here is that list from terminal
---------------------------------
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
bjarki@bjarki:~$ 
----------------------------------------
know I look at fstab.

---

### Post by richardjennings on 2008-07-27
that looks fine, 

probably best to restart your computer now to see if Ubuntu will automatically mount the drive. If it doesn't, you can add a fstab entry.

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> that looks fine, 

probably best to restart your computer now to see if Ubuntu will automatically mount the drive. If it doesn't, you can add a fstab entry.
Hi again I did restart my pc and now my file browser can see that disk and I right click on it to unmount him but take a look on that photo. I am just where I was from beginning
I am learning a lot from you but I dont know why I can not cope into that disk.

---

### Post by richardjennings on 2008-07-27
ok no worries

make the folder you want to mount the drive into, for example:


```
mkdir /media/disk2
```


add this line to your /etc/fstab

```
/dev/sdb1  /media/disk2 ext3    defaults        0       2
```

unmount /media/disk

```
sudo umount /media/disk
```

mount the new fstab entry

```
mount
```

any luck?

---

### Post by gretarsson on 2008-07-27
> **richardjennings said:**
> ok no worries

make the folder you want to mount the drive into, for example:


```
mkdir /media/disk2
```


add this line to your /etc/fstab

```
/dev/sdb1  /media/disk2 ext3    defaults        0       2
```

unmount /media/disk

```
sudo umount /media/disk
```

mount the new fstab entry

```
mount
```

any luck?
--------------------------------
Hi again, no luck see picture.

Here is what I did in terminal:

bjarki@bjarki:~$ mkdir /media/disk2
mkdir: cannot create directory `/media/disk2': Permission denied
bjarki@bjarki:~$ sudo mkdir /media/disk2
[sudo] password for bjarki: 
bjarki@bjarki:~$ gksudo gedit /etc/fstab
bjarki@bjarki:~$ sudo umount /media/disk
bjarki@bjarki:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-20-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bjarki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bjarki)
bjarki@bjarki:~$ 
----------------------------------------------------------------
and here is how fstab look like, I just coped your line but is the space not to big.

bjarki@bjarki:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b54e307-65a8-4b8d-8b68-a6100071e046 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=898d45f4-e0d5-463d-9fc9-70377542f6bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#dev#sdb
/dev/sdb1  /media/disk2 ext3    defaults        0       2

---

### Post by Elfy on 2008-07-27
Unless you've rebooted you need to tell it to mount the disk

```
sudo mount -a
```

Then check it's there with

```
df -h
```

---

### Post by ezsit on 2008-07-28
gretarsson wrote:
> I am learning a lot from you but I dont know why I can not cope into that disk.

No offense gretarsson, I gave you six steps back on page two that would have given you exactly what you wanted, except for eliminating the second swap partition. Now that you deleted the extra swap, here are steps you can copy and paste, and at the end of the process have a working solution.

[B]Step one, unmount the partition:
sudo umount /dev/sdb1[/B]

[B]Step two, format the partition:
sudo mkfs.ext3 /dev/sdb1[/B]

EDIT - I know the partition is already formatted, so this is just for good measure, or unnecessary, either way.

[B]Step three, create a mountpoint: 
sudo mkdir /mnt/new_disk[/B]

EDIT - I never use /media since the system has uses for /media and I do not want any confusion between the system and my own use.

[B]Step four, mount the partition:
sudo mount /dev/sdb1 /mnt/new_disk[/B]

[B]Step five, change ownership of the mountpoint:
sudo chown *yourusername:yourusername* /mnt/new_disk[/B]

EDIT - Substitute your own username in the above example:
gretarsson:gretarsson

[B]Step six, add this line to your fstab:
/dev/sdb1   /mnt/new_disk   ext3   defaults,rw   0 0
[/B]
It should be no more complicated than this.

---

