---
title: "Can't read windows partition anymore?"
date: 2008-11-01
forum: General Help
---

### Post by personjerry on 2008-11-01
I used to be able to mount my windows partition and read it easily, and now when I mount it there is nothing in there. I checked GParted, and it stated that it is unable to read the contents of the filesystem.

This may or may not be connected: A while back, I installed SP3 on the windows partition (XP). It worked for a while, then one day when I booted the Blue Screen Of Death came up and said some drivers weren't working. From then on, every time I booted in windows that screen would come up. However, I could still read the partition in Ubuntu, until recently.

Anyone know how to solve this?

---

### Post by personjerry on 2008-11-02
bump.

---

### Post by personjerry on 2008-11-03
Bump
Ump
Mp
P

---

### Post by taurus on 2008-11-03
Maybe the last time you used it, it was not unmounted cleanly so you won't be able to mount it again without using the force option.  

What is the error message if you try to mount it by hand, assuming your windows partition is **/dev/sda1**?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g **/dev/sda1** /media/windows
```

---

### Post by personjerry on 2008-11-04
The partitions are mountable without the -f option. And my windows partition is sda2. And what happens when I mount manually is the same thing, empty folder.

---

### Post by taurus on 2008-11-04
What's the output of this command then?

```
df -h
```

---

### Post by personjerry on 2008-11-04
```
jerry@Jerrys-System:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              78G   42G   32G  57% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  356K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.8M  249M   2% /dev
tmpfs                 251M     0  251M   0% /dev/shm
lrm                   251M  2.0M  250M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda1             4.9G  4.2G  764M  85% /media/boot
/dev/sda2              64G   67M   64G   1% /media/disk
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0
/dev/sda2              64G   67M   64G   1% /media/windows
jerry@Jerrys-System:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              78G   42G   32G  57% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  356K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.8M  249M   2% /dev
tmpfs                 251M     0  251M   0% /dev/shm
lrm                   251M  2.0M  250M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda1             4.9G  4.2G  764M  85% /media/boot
/dev/sda2              64G   67M   64G   1% /media/disk
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0
/dev/sda2              64G   67M   64G   1% /media/windows
jerry@Jerrys-System:~$ 


```

---

### Post by taurus on 2008-11-04
The window partition is empty alright.

```
/dev/sda2              64G   67M   64G   1% /media/windows
```
Did you do anything to /dev/sda2 when you installed Ubuntu?

Can you also post the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by personjerry on 2008-11-04
as I said, it was still readable and writable until a few weeks back.

```
jerry@Jerrys-System:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xdd5bdd5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         674     5095408+   b  W95 FAT32
/dev/sda2             675        9536    66996720    7  HPFS/NTFS
/dev/sda3            9537       20473    82683720   83  Linux
/dev/sda4           20474       20673     1512000    5  Extended
/dev/sda5           20474       20673     1511968+  82  Linux swap / Solaris
jerry@Jerrys-System:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=38d670dc-f26d-4316-b0b6-48aa1877d462 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8bd6908c-ad55-4716-9eb6-cfdbcd7a84a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /media/boot     vfat users,rw,umask=0 0 0
/dev/sda2       /media/disk     ntfs users,rw,force,umask=0 0 0
jerry@Jerrys-System:~$ 

```

---

### Post by taurus on 2008-11-04
Looks like /media/windows and /media/disk are the same thing--/dev/sda2.  It's not a good idea to force mount an ntfs partition every single time.  So I guess if you want to run windows again, you just have to reinstall it since you got the blue screen of death anyway.

Or better yet, convert /dev/sda2 to ext3 filesystem and use it as a storage space for Ubuntu.  What do you have in /dev/sda1--/media/boot (fat32)?

---

### Post by personjerry on 2008-11-04
hp's system restore :D
so if i can't fix windows with some other form of archive i had installed there i'll see what that does.

---

### Post by personjerry on 2008-11-07
But does anyone have a different solution? I wouldn't like to lose all my data...

---

### Post by personjerry on 2008-11-09
Bump
Ump
Mp
P

---

### Post by personjerry on 2008-11-10
bump!!!

---

### Post by personjerry on 2008-11-11
bump yet again!!!!

---

### Post by personjerry on 2008-11-12
buuuuuuuump

---

### Post by john183 on 2008-11-12
Just going on my windows experience alone, if you were getting the BSOD in winxp w/sp3 then your partition is shot. in all the time that i have been using win2k & xp (since it came out) i have never gotten a BSOD without the drive/partition being totally jacked up. and i have done some totally messed up things in windows. I used to go and mess with files and settings just to see what would totally screw up the os. WinME was WIN OS to BSOD on me without scrapping the drive. I think you may have completely lost that partition, sorry.

---

### Post by personjerry on 2008-11-13
Yet Another Bump

---

### Post by daximus on 2008-11-13
Given the BSOD and 'drive error' problem in Windows, I would guess that your drive is failing and may have lost either index, or the data itself.

---

### Post by personjerry on 2008-11-13
so not fixable :( ?

---

### Post by personjerry on 2008-11-14
aw well that sucks... guess I'll try restores soon... in the meantime, feel free to suggest how ELSE to solve this!!

---

