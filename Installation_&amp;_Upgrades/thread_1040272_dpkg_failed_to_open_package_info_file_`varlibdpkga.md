---
title: "dpkg: failed to open package info file `/var/lib/dpkg/available' for reading"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Nandi on 2009-01-15
Hallo Honorable members,
I am a very very new person to Ubuthu. My problem: I was trying to update this is error I got : 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to search around but it seem I am experiencing a special problem because when I try to run sudo dpkg --configure -a this is what I get:

nandi@pg-179:~$ sudo dpkg --configure -a
[sudo] password for nandi: 
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-ubuntu-modules-2.6.24-22-generic (2.6.24-22.35) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
dpkg: subprocess post-installation script returned error exit status 1

PLEASE help!

---

### Post by zwygart on 2009-01-15
Welcome to ubuntu,

It says that you don't have enough space. 
post the output of df.

This will say what is mounted where and if it have space.

---

### Post by Nandi on 2009-01-15
[COLOR="Blue"]Zwygart[/COLOR],
Thanks in advance for interest to help. As I wrote am brand new to this OS so when you give me instructions please include the code (copy and paste).
Thanks again

---

### Post by Nandi on 2009-01-16
Is this the correct way to do it?
nandi@pg-179:~$ sudo df
[sudo] password for nandi: 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             23253940   5890172  16191828  27% /
varrun                 1677276       120   1677156   1% /var/run
varlock                1677276         0   1677276   0% /var/lock
udev                   1677276        96   1677180   1% /dev
devshm                 1677276        12   1677264   1% /dev/shm
lrm                    1677276     43040   1634236   3% /lib/modules/2.6.24-18-generic/volatile
/dev/sda1                93307     91034         0 100% /boot
/dev/sda6            214992984  17318116 186839832   9% /home

I hope this is the info you want to analyse...

Thank u in advance

---

### Post by zwygart on 2009-01-19
All right this is what I wanted. ;)

First, you wanted to update. Have you ran ```
sudo apt-get update
```.
Second as I expected, you don't have enough space on your boot partition (The 100% in df). This prevent of installing the new image of ubuntu to the partition. And the configuration of the others packages wich depends on.

The easiest way to try to fix this is to grow the partition. You have enough space. So to do this the easy way, go in system>administrator>Gnome partition editor. This shows you the partition on your drive. Localise the one called sda1. You probably need to unmount it (Right click>unmount). Then increase the size. You have 93M wich is not a lot. Grow it to 200M minimum (I suggest 500M). You may need to shrink the partition beside. After that try again to update like you said.

If this doesn't work, please post the output like before of ```
sudo df -h
sudo fdisk -l
```

Sorry to be late. I don't have Internet at weekends

---

### Post by Nandi on 2009-01-20
Unfortunately i was not able to do the first task because under system>administrator>there is no link to: Gnome partition editor. In other words there is no option where i could select Gnome partition editor. The option results are as follows:

nandi@pg-179:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              23G  5.7G   16G  27% /
varrun                1.6G  120K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G   88K  1.6G   1% /dev
devshm                1.6G   24K  1.6G   1% /dev/shm
lrm                   1.6G   43M  1.6G   3% /lib/modules/2.6.24-18-generic/volatile
/dev/sda1              92M   89M     0 100% /boot
/dev/sda6             206G   17G  179G   9% /home
/dev/sdb2              44G  2.1G   40G   5% /media/disk
/dev/sdb1             187G   72M  187G   1% /media/disk-1
nandi@pg-179:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         498     3903795   82  Linux swap / Solaris
/dev/sda3             499       30394   240139620    5  Extended
/dev/sda5             499        3416    23438803+  83  Linux
/dev/sda6            3417       30394   216700753+  83  Linux

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24316   195318238+   7  HPFS/NTFS
/dev/sdb2   *       24317       30140    46781280   83  Linux
/dev/sdb3           30141       30394     2040255    5  Extended
/dev/sdb5           30141       30394     2040223+  82  Linux swap / Solaris


Thank u for taking your time to help
nandi

---

### Post by Kevbert on 2009-01-20
If you enter the following in terminal you'll probably find that there are a number of kernels that you don't use:
```
cd /boot
ls -l
```
The output will be something like this:
```
-rw-r--r-- 1 root root  420395 2008-11-24 22:19 abi-2.6.24-22-generic
-rw-r--r-- 1 root root  420395 2008-11-27 20:56 abi-2.6.24-23-generic
-rw-r--r-- 1 root root   74177 2008-11-24 22:19 config-2.6.24-22-generic
-rw-r--r-- 1 root root   74166 2008-11-27 20:56 config-2.6.24-23-generic
drwxr-xr-x 2 root root    4096 2009-01-09 08:13 grub
[COLOR="Red"]-rw-r--r-- 1 root root 8169231 2008-12-08 07:40 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 8169048 2009-01-14 11:09 initrd.img-2.6.24-23-generic
-rw-r--r-- 1 root root 8169676 2009-01-10 17:42 initrd.img-2.6.24-23-generic.bak[/COLOR]
-rw-r--r-- 1 root root  103204 2007-09-28 12:03 memtest86+.bin
-rw-r--r-- 1 root root 1153201 2008-11-24 22:19 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1153225 2008-11-27 20:56 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1905656 2008-11-24 22:19 vmlinuz-2.6.24-22-generic
-rw-r--r-- 1 root root 1907096 2008-11-27 20:56 vmlinuz-2.6.24-23-generic

```
From this you can see that I have three kernels which are highlighted - 2.6.24-22 2.6.24-23 and 2.6.24-23.bak.
You can remove any .bak kernels with
```
sudo rm *.bak
```
Be careful that you enter it as shown.
Now any remaining kernels which you don't use you can get rid of. It's always best to keep the previous kernel in case of problems.  I'm using 2.6.24-23 and so need to keep 2.6.24-22.  The kernels are normally shown when you boot up the PC in the grub menu.  To delete an old kernel make a note of the number and then open Synaptic Package Manager. Search for linux-image and then mark the kernel you want to get rid of for complete removal (e.g. linux-image-2.6.24.21-generic) and click on Apply.  You should now have some room in your boot partition.

---

### Post by zwygart on 2009-01-20
Sorry, I missed some thing.
Try the thing of Kevbert.
To have Gnome partition editor you can boot from a LiveCD. This is the easiest way because you can do everything and the partition editor is there by default. You may also install it trought synaptic. It's real name is gparted. (Terminal : sudo apt-get gparted)

If you are unable to do what Kevbert says and to resize partition, they is a possibility to move the kernels and initrd.img to another partition. But this is not easy the first time. Hope that this works.

---

### Post by Partyboi2 on 2009-01-20
I would follow Kevbert suggestion and remove the old kernels that are know longer needed. 
If in the future you plan to do partitioning work for what ever reason you will need to use a Ubuntu live cd or gparted live cd as the drives need to be unmounted to work on partitions. :D

---

### Post by Kevbert on 2009-01-21
As the last two posters have suggested it's worth having a partition editor such as gparted installed for manipulating your drives. You can get it via Synaptic Package Manager.

---

### Post by Nandi on 2009-01-21
Hi everyone
You all deserve a big hug. With your suggestions I managed to resolve the problem and now it is working perfectly. I love you all.

Cheers
nandi

---

