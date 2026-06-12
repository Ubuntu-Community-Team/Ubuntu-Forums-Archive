---
title: "When i try to hibernate on my laptop, it says there isnt enough free swap."
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by systemintheglitch on 2006-10-03
I chose the recommended amount on the install. what gives:?

---

### Post by bigken on 2006-10-03
how much ram do you have and what size is your swap file

the safest bet for a swap file is twice your ram you can resize your swap file using [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD

---

### Post by systemintheglitch on 2006-10-03
> **bigken said:**
> how much ram do you have and what size is your swap file

the safest bet for a swap file is twice your ram you can resize your swap file using [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD


I have 275mb swap and 700 something mb ram.

---

### Post by bigken on 2006-10-03
you have 768mb ram so you need 1.5gig of swap use the gparted live cd delete your swap and create a new with enough space ;)


or take some of your root or home partion (downsize) and make your swap bigger

---

### Post by systemintheglitch on 2006-10-03
> **bigken said:**
> you have 768mb ram so you need 1.5gig of swap use the gparted live cd delete your swap and create a new with enough space ;)


So what is the point of swap partition?? Why doesnt windows require it? Does it just hide its swap partition?

---

### Post by bigken on 2006-10-03
windows does its check it your self in hibernate (disc space required to hibernate 511mb)  and it also needs a virtual memory 768mb ;)

---

### Post by strabes on 2006-12-08
if I have no swap partition and I create one with the gparted live CD will ubuntu automatically recognize it so that I will be able to hibernate my computer?

---

### Post by strabes on 2006-12-11
bump

---

### Post by systemintheglitch on 2006-12-13
Good question strabes.. I would like to know this too.


Also: Why should I have to declare it as a partition? Windows requires the disk space, but doesn't require that you have a particular partition for it!

Can we configure ubuntu to behave like this?

---

### Post by zgornel on 2006-12-13
Linux is not Windows. Windows puts the memory contents to a file, Linux to a swap partition. The swap partition has to be at least as large as the amount of memory installed on the system. To create a swap partition use GParted or boot with the Live CD ad do the work from there.
After you made the partition (formatted it), right click it and choose the *swapon* option. Check */dev/disk/by-uuid* for a symlink that points to the partition (do a ls -l in that directory) and write it down. Edit */etc/fstab* accordingly (add this line):
```
UUID=<uuid of partition> swap sw 0 0 
```
Edit */etc/initramfs-tools/conf.d/resume* and put the line 
```
RESUME=UUID=<uuid of partition>
```
Reboot.
Try to hibernate.

---

### Post by strabes on 2006-12-13
Ok that's good to know, but the problem is that I already have four primary partitions on my hard drive, and I can't make any more. I don't really understand the concept of extended partitions, so could someone explain to me how I should set up my partition system so I have the following:

| Windows | Shared ext3 | Linux | swap | /home |
or
| Windows | Shared ext3 | Linux | /home | swap |

I'd prefer to not have to format any partitions, but if it is necessary to do so, could I make the shared partition smaller, and then move all the partitions to the left in order to make room for the swap area?

---

### Post by zgornel on 2006-12-13
> **strabes said:**
> Ok that's good to know, but the problem is that I already have four primary partitions on my hard drive, and I can't make any more. I don't really understand the concept of extended partitions, so could someone explain to me how I should set up my partition system so I have the following:

| Windows | Shared ext3 | Linux | swap | /home |
or
| Windows | Shared ext3 | Linux | /home | swap |

I'd prefer to not have to format any partitions, but if it is necessary to do so, could I make the shared partition smaller, and then move all the partitions to the left in order to make room for the swap area?

What you must do is to transform your home partition (which is primary now) into a extended partition. A extended partition is a primary partition that supports more partitions inside itself. After transforming /home into an extended partition, resize it in order to create space for the swap partition. Post a Gparted screenshot with current partition config.

---

### Post by strabes on 2006-12-14
Would transforming my home partition into an extended partition require me to format it? Here's a screenshot showing my current partition setup:

---

### Post by zgornel on 2006-12-14
I think Gparted cannot transform a primary partition into a logical one so you have to:
1/ Backup Data from /dev/sda2 to the other partitions.
2/ Delete /dev/sda2
3/ Create an extended partition in the free space (it will be named /dev/sda2)
4/ Create a 1-2 GB swap logical partition and another data logical partition inside the extended partition
(Logical partitions are created inside extended partitions)
In the end you'll end up with 6 partitions:
3 that you had before, 1 extended and 2 other inside the extended one. 
It is important that you modify /etc/fstab accordingly. 
Good luck ! :D

---

### Post by strabes on 2006-12-14
Ok thanks for the help. I'm backing up my data to my ipod right now and then I'll boot into the gparted live cd. I'll let you know how it turns out.

---

### Post by BLTicklemonster on 2006-12-14
I can't hibernate on my desktop either. there's not enough space. I keep falling off. 


:(




(okay, sorry, I'll leave you all alone)

---

### Post by strabes on 2006-12-14
Ok I did everything and modified my fstab. Now I need to know how to enable/mount the swap partition. Here's another screenshot:

---

### Post by zgornel on 2006-12-15
Good. Right click on it and choose the *swapon* option. Afterwords, go to my first post here and follow instructions. After reboot, hibernate should work. You can always check if swap is used with *free -m* command. Good luck.

---

### Post by strabes on 2006-12-15
OK I did all that and the only thing that happens when I hit hibernate is that it locks my screen, shows the window to unlock it, and disconnects me from my wireless network. When I re-login it *does* reconnect to the wireless so that's not a problem. /dev/sda6 is my swap partition. Here's some stuff:

 ls -l /dev/disk/by-uuid/
> 
total 0
lrwxrwxrwx 1 root root 10 2006-12-15 06:41 236c6fd6-2c2a-447c-a586-8b995c01864b -> ../../sda5
lrwxrwxrwx 1 root root 10 2006-12-15 06:41 AA1C2D5E1C2D26B3 -> ../../sda1
lrwxrwxrwx 1 root root 10 2006-12-15 06:41 b461a9b8-6d84-4ddf-aaa7-1cd23b86996a -> ../../sda3
lrwxrwxrwx 1 root root 10 2006-12-15 06:41 b8e3851e-c1fa-4838-bf53-85aa1e431cba -> ../../sda6
lrwxrwxrwx 1 root root 10 2006-12-15 06:41 d3929551-e00e-47cd-b078-1d7afc28b396 -> ../../sda4


/etc/fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda3
UUID=b461a9b8-6d84-4ddf-aaa7-1cd23b86996a  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda4
UUID=d3929551-e00e-47cd-b078-1d7afc28b396  /home          ext3         defaults                    0  2  
/dev/sda3                                  /media/sda3    ext3         defaults                    0  0  
/dev/sda4                                  /media/sda4    ext3         defaults                    0  0  
/dev/sda5                                  /media/data    ext3         defaults   0  0
#/dev/sda6
UUID=b8e3851e-c1fa-4838-bf53-85aa1e431cba  none           swap         sw         0  0
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto                 0  0  


/etc/initramfs-tools/conf.d/resume
> RESUME=UUID=b8e3851e-c1fa-4838-bf53-85aa1e431cba

free:
> 
             total       used       free     shared    buffers     cached
Mem:       1034488     595872     438616          0      15676     276112
-/+ buffers/cache:     304084     730404
Swap:      2096440          0    2096440

So obviously my swap is being recognized, but not really used...? Thanks for all your help.

---

### Post by zgornel on 2006-12-15
THere is no problem with swap. The swap is used when you run out of memory. If you open alot of programs you'll notice that swap is used. So, from what I understand it does not hibernate ? Everything seems to be in place. Run *sudo update-initramfs*, reboot and retry to hibernate.

---

### Post by strabes on 2006-12-16
when i type that in i get this: 

> 
alex@alex-laptop:~$ sudo update-initramfs -U
Illegal option -U
Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]   Specify kernel version or all
 -c             Create a new initramfs
 -u             Update an existing initramfs
 -d             Remove an existing initramfs
 -t             Take over a custom initramfs with this one
 -b             Set alternate boot directory
 -v             Be verbose
 -h             This message


which one should i do?

---

### Post by zgornel on 2006-12-16
Try -c.

---

### Post by strabes on 2006-12-16
alright with the -c flag here's what I get:

> 
alex@alex-laptop:~$ sudo update-initramfs -c
Create mode requires a version argument

Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]   Specify kernel version or all
 -c             Create a new initramfs
 -u             Update an existing initramfs
 -d             Remove an existing initramfs
 -t             Take over a custom initramfs with this one
 -b             Set alternate boot directory
 -v             Be verbose
 -h             This message


---

### Post by zgornel on 2006-12-17
sudo update-initramfs -u -k 2.6.17-10-generic

---

### Post by strabes on 2006-12-17
ok I did that and rebooted my computer and nothing has changed when I try to hibernate :(

---

### Post by zgornel on 2006-12-17
Can't understand why it does not work because it shoud :confused:  . As a last resort, install the hibernate script: ```
sudo apt-get install hibernate
``` and try hibernating using it: ```
sudo hibernate
```.

---

### Post by strabes on 2006-12-17
Ok I ran that and I get this pastel colored screen and it hard locks & I have to cold reboot. This is kinda ridiculous...I have a Dell E1705...This series of laptops is pretty much the most popular out there...I think this should kinda be a priority for the developers....

---

### Post by zgornel on 2006-12-18
I dunno what to make of it. Just to make sure, recheck to that the name of the simlink that points to the swap partition is the same for all the files. Also, add ```
resume=UUID=<swap uuid>
``` in the kernel line present in /boot/grub/menu.lst and retry hibernating.

---

### Post by strabes on 2006-12-18
got that and it's still not working. oh well I'm pretty much giving up. Maybe it will just work in feisty

---

### Post by Carsto on 2008-01-11
I am Johnny come lately on this topic. Only now got into things Linux.  I give this so the difference between MS and Linux may be easier to understand for guys doing the change-over.

The Windows "Swap partition" is called virtual memory or a page file system.  This simply means it is reserved memory where jobs can be done repetitively.  It is virtual memory since the same real estate is used for the data needed by various jobs. Look in Device Manager or related (sorry, time caught up, I can't find the exact spot) to change the size - usually RAM x 2.5 maximum.

Take any file you normally edit and is already saved to disc.  Do Alt-a,f.a.  A dialog will show telling you that file already exists, do you want to overwrite it?   Swap works like this, but automatically.

The 503 MB needed to hibernate is written to disc.  It is not swap memory, it is the settings you see being saved before you PC hibernates. Otherwise it will not know what your prefs are when it wakes up.

---

