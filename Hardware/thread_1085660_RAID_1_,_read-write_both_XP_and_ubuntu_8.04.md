---
title: "RAID 1 , read-write both XP and ubuntu 8.04"
date: 2009-03-03
forum: Hardware
---

### Post by T3rmInAt0r on 2009-03-03
Hi guys, I am new to this forum (but I had used it many times in past as citation :)) Congrats for your great work.

I am running a serious problem about my system.
I have 4 SATA devices:

1 HD (raptor) 150GB  [ contains xp , 8.04 dual boot ] - SATA0
1 DVD-RW - SATA1
2 HD 750 GB [new for RAID 1] - SATA2 , SATA3

I connected the new drivers in my mobo (gigabyte  GA-8N-SLI Royal). Activate RAID controller (nVIDIA) and made the RAID 1 arrays.

In windows I installed the RAID controller. The OS recognize the 2 disks as 1 (as it supposed to be), formatted in NTFS, Read-write OK. RAID 1 in widows OK!

Now when I boot in 8.04, the OS recognize the disks as two separate disks tha have the same name (I named them RAID for ease). So now I have 2 RAID disks, each one in NTFS. First, I thought that, it would be just implementation bug. BUT when I wrote something to the 1st disk, the same file hadn't been written to the 2nd disk, as well.... SO the "problem" is simple.... RAID doesn't work.
I say some pages such as [http://lxr.linux.no/linux/Documentation/ldm.txt](http://lxr.linux.no/linux/Documentation/ldm.txt) and [http://lxr.linux.no/linux/Documentation/filesystems/ntfs.txt](http://lxr.linux.no/linux/Documentation/filesystems/ntfs.txt) but... I couldn't figure out a solution. With some times googling... I found the [http://ubuntuforums.org/showthread.php?t=629459](http://ubuntuforums.org/showthread.php?t=629459) . Since I didn't noticed any spot that reffers exclusively on RAID 0, I followed the instructions.
dmraid -ay etc....
everything went fine and without problem
BUT!!!! now that I try to mount the disk a message erro apears 
**fuse: mount failed: Device or resource busy**

Now, I try to make the fstab to mount the disks as NTFS and to use them as it was supposed to be...AT THIS POINT I NEED some help... I can't go on

Thanx anyone who read me, in advance.

some more info

----------------------------------------------------
t3rminat0r@Exterminator:~$ less  /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3f745f73-4bd3-4098-956e-1312ae7061fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=15667e6e-95f1-4ba4-9256-740d339ff754 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/mapper/nvidia_cdibcbcj 
#/media/ntfs auto rw,user,noauto,exec,utf8 0       0


----------------------------------------------------

t3rminat0r@Exterminator:~$ sudo dmraid -ay
[sudo] password for t3rminat0r: 
RAID set "nvidia_cdibcbcj" already active
RAID set "nvidia_cdibcbcj1" already active

----------------------------------------------------
t3rminat0r@Exterminator:~$ cat /proc/partitions
major minor  #blocks  name

   8     0  146523384 sda
   8     1  111908758 sda1
   8     2          1 sda2
   8     5   33559753 sda5
   8     6    1052226 sda6
   8    16  732574584 sdb
   8    17  732571648 sdb1
   8    32  732574584 sdc
   8    33  732571648 sdc1
 254     0  732574583 dm-0
 254     1  732572001 dm-1


----------------------------------------------------

when I try 

t3rminat0r@Exterminator:/mnt$ sudo mount /dev/mapper/nvidia_cdibcbcj
[sudo] password for t3rminat0r: 
mount: mount point  does not exist

---

### Post by Coreigh on 2009-03-03
Most inexpensive RAID cards and built-in RAID controllers are actually software RAID,... of some type. I do not know specifically for your mobo if this is true. However if it is you will not get RAID to work for both OS's unless someone has created a RAID controller driver for your RAID chipset to work with Linux. As I understand it although both Windows and Linux can utilize software RAID, they use two very different methods.

Keep in mind I am not saying it isn't possible but I think that to make it work you will have to have your Linux OS be able to understand Windows software RAID.

---

### Post by T3rmInAt0r on 2009-03-03
> **Coreigh said:**
> Most inexpensive RAID cards and built-in RAID controllers are actually software RAID,... of some type. I do not know specifically for your mobo if this is true. However if it is you will not get RAID to work for both OS's unless someone has created a RAID controller driver for your RAID chipset to work with Linux. As I understand it although both Windows and Linux can utilize software RAID, they use two very different methods.

Keep in mind I am not saying it isn't possible but I think that to make it work you will have to have your Linux OS be able to understand Windows software RAID.

Indeed it is software raid. My mobo has two raid controllers nVIDIA and Promise. I used nVIDIA. I want to use the controller build-in my mobo (not to buy an extra one)

I was told about FreeNAS and other couple of solutions. BUT I have ONLY 1 PC and I can't but any new componet. So I have to make somethig with the ones I already have.

---

