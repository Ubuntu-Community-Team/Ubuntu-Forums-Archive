---
title: "Okay I need just really direct, no jargon, directions on how to mount /dev/sda6"
date: 2008-11-26
forum: General Help
---

### Post by gaalaaant on 2008-11-26
okay, I have already posted about this here, and I hope no one is upset, but I read all that tutorials, and I don't understand any of it.

I will post any thing you ask as long as I can get direct, step by step, directions on how to mount my /dev/sda6 ( my music, movies, and pictures) and where to do it. I've tried posting both here and yahoo answers and people were very nice and very helpful but I am afraid I didn't totally grasp what they said  guess because none of it worked. I need like step by step, idiot proof directions.  I will post anything that is needed but just to start off with here I go:

daniel@daniel-laptop:~$ cat /etc/mtab
/dev/sda1 / jfs rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda5 /home xfs rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/daniel/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=daniel 0 0



also. just a question and I don't mean to question the makers of this but, why is it necessary to make people manually mount things? why can't it just be more like windows where a partition or cd just pops up when you pop it in?

---

### Post by tang0delta on 2008-11-26
Hi gaalaaant.

You seem pretty frustrated with this lol. It's understandable. People who are new to linux often run into these types of problems. I myself have and still do occasionally. I do believe your problem can be fixed but first I need you to describe the problem very clearly. Is the drive you are trying to mount a removable drive(like a usb external) or is it inside your computer, what is the filesystem of the drive (ntfs, fat32 etc..) 

--
tang0delta

---

### Post by wirelessmonkey on 2008-11-26
Step-by-step

open a terminal
type:

sudo mkdir /media/mystuff
sudo mount /dev/sda6 /media/mystuff

If this doesn't work, post the error message received.
If no errors, your stuff will be in /media/mystuff. Depending on what format your drive is, we may have to change permissions on it, so try to read and write files to the drive.  Post if it does or does not work.  If it does work, we'll edit your fstab file so the drive mounts automatically on reboot.

---

### Post by gaalaaant on 2008-11-26
this is the error I got

daniel@daniel-laptop:~$ sudo mkdir /media/mystuff
[sudo] password for daniel: 
daniel@daniel-laptop:~$ sudo mount /dev/sda6 /media/mystuff
/dev/sda6 looks like swapspace - not mounted
mount: you must specify the filesystem type
daniel@daniel-laptop:~$ 
daniel@daniel-laptop:~$

---

### Post by nzadLithium on 2008-11-26
fdisk -l post output here plz :)

---

### Post by gaalaaant on 2008-11-26
daniel@daniel-laptop:~$ fdisk -l
Cannot open /dev/sda
daniel@daniel-laptop:~$ 
daniel@daniel-laptop:~$

---

### Post by sisco311 on 2008-11-26
do you want to mount the partition automatically at boot time?

please post the output of:
```
sudo fdisk -l
```
```
sudo blkid
```and
```
cat /etc/fstab
```

---

### Post by gaalaaant on 2008-11-26
> **sisco311 said:**
> do you want to mount the partition automatically at boot time?

please post the output of:
```
sudo fdisk -l
```
```
sudo blkid
```and
```
cat /etc/fstab
```
1.
daniel@daniel-laptop:~$ sudo fdisk -l
[sudo] password for daniel: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbadfab80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        3040    14651280    b  W95 FAT32
/dev/sda3            3041       19453   131837422+   5  Extended
/dev/sda5            3163       19453   130857426   83  Linux
/dev/sda6            3041        3162      979902   82  Linux swap / Solaris

Partition table entries are not in disk order


2.

daniel@daniel-laptop:~$ sudo blkid
/dev/sda1: UUID="98e55dee-122f-482d-bc1e-69039449706d" TYPE="jfs" 
/dev/sda2: UUID="64E4-CE3B" TYPE="vfat" 
/dev/sda5: UUID="5a2976d5-ae68-4a6f-8153-4eb97a8c405f" TYPE="xfs" 
/dev/sda6: TYPE="swap" UUID="8aae3c7d-ee46-437b-8849-ddf4b157da00" 


3.

daniel@daniel-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98e55dee-122f-482d-bc1e-69039449706d /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5a2976d5-ae68-4a6f-8153-4eb97a8c405f /home           xfs     relatime        0       2
# /dev/sda6
UUID=8aae3c7d-ee46-437b-8849-ddf4b157da00 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Wally_dog on 2008-11-26
I found a very good guide to mounting partitions awhile ago... Basically, I mounted the partition, had a link from Music to Music in the partition, same with videos etc. If I find it I'll post it here, k?

---

### Post by sisco311 on 2008-11-26
edit the fstab:
```
gksu gedit /etc/fstab
```and add a new entry:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=98e55dee-122f-482d-bc1e-69039449706d / jfs relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=5a2976d5-ae68-4a6f-8153-4eb97a8c405f /home xfs relatime 0 2
# /dev/sda6
UUID=8aae3c7d-ee46-437b-8849-ddf4b157da00 none swap sw 0 0
[b]# /dec/sda2
UUID=64E4-CE3B /media/*name* vfat defaults,umask=002,gid=46 0 0[/b]
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

create the mount point:
```
sudo mkdir /media/*name*
```

mount the partition:
```
sudo mount -a
```

you can change the mount point(/media/*name*) to whatever you want(ex. /media/music).

the partition will mount automatically on next boot.

---

### Post by unutbu on 2008-11-26
Type```

sudo mkdir /Win
gksu gedit /etc/fstab
```

Add these lines to the bottom of the file
```
#/dev/sda2
UUID=64E4-CE3B /Win vfat defaults,user,uid=1000,dmask=027,fmask=137 0 2
```

save and exit gedit.

Type
```

sudo mount /Win
```

Your windows directory will now be mounted at /Win

If this is successful, from now on when you boot up the windows directory will be 
automatically mounted at /Win.

---

### Post by uldo on 2008-11-26
Can you post what I should add for the NTFS to mount automaticly? I tried to edit by my self some time ago but it didnt work :(

```
sudo fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde74de74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38164   306552298+  83  Linux
/dev/sda2           38165       38913     6016342+   5  Extended
/dev/sda5           38165       38913     6016311   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15731572

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS

```

```
sudo blkid
/dev/sda1: UUID="a87d0970-e165-4ddd-ad81-7cf97cfaa251" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="67fd8251-e000-41bd-89ed-3f3ce0f19b93" 
/dev/sdb1: UUID="1C845F14845EF02E" TYPE="ntfs" 

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a87d0970-e165-4ddd-ad81-7cf97cfaa251 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=67fd8251-e000-41bd-89ed-3f3ce0f19b93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by gaalaaant on 2008-11-26
god i hope this works ^_^, just gotta finish hw, ill post back with the results!

---

### Post by sisco311 on 2008-11-26
> **uldo said:**
> Can you post what I should add for the NTFS to mount automaticly? I tried to edit by my self some time ago but it didnt work :(

```
sudo fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde74de74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38164   306552298+  83  Linux
/dev/sda2           38165       38913     6016342+   5  Extended
/dev/sda5           38165       38913     6016311   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15731572

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS

```

```
sudo blkid
/dev/sda1: UUID="a87d0970-e165-4ddd-ad81-7cf97cfaa251" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="67fd8251-e000-41bd-89ed-3f3ce0f19b93" 
/dev/sdb1: UUID="1C845F14845EF02E" TYPE="ntfs" 

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a87d0970-e165-4ddd-ad81-7cf97cfaa251 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=67fd8251-e000-41bd-89ed-3f3ce0f19b93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
> UUID=1C845F14845EF02E */media/mount-point* ntfs defaults,umask=002,gid=46 0 0 

don't forget to create the mount point:
```
sudo mkdir */media/mount-point*
```

---

### Post by gaalaaant on 2008-11-26
okay so it worked but it was the wrong partition (the 15 gb instead of the 130 gb), is there any way i can mount the 130 instead of the 50? do i just follow all those steps again? sorry , i goofed, but i was really damn sure it was dev/sda6 and not 5 or 2.

ill try 5 next, but is all i do the same thing just replace it with 5 instead?

---

### Post by uldo on 2008-11-26
thanks that woked!!! gaalaaant - change the UUID when changing numbers!!! according to this:

daniel@daniel-laptop:~$ sudo blkid
/dev/sda1: UUID="98e55dee-122f-482d-bc1e-69039449706d" TYPE="jfs"
/dev/sda2: UUID="64E4-CE3B" TYPE="vfat"
/dev/sda5: UUID="5a2976d5-ae68-4a6f-8153-4eb97a8c405f" TYPE="xfs"
/dev/sda6: TYPE="swap" UUID="8aae3c7d-ee46-437b-8849-ddf4b157da00"

---

### Post by sisco311 on 2008-11-26
> **gaalaaant said:**
> okay so it worked but it was the wrong partition (the 15 gb instead of the 130 gb), is there any way i can mount the 130 instead of the 50? do i just follow all those steps again? sorry , i goofed, but i was really damn sure it was dev/sda6 and not 5 or 2.

ill try 5 next, but is all i do the same thing just replace it with 5 instead?

/dev/sda5 is your /home partition
/dev/sda1 is the root ("/") partition and
/dev/sda6 is the swap partition

did you format the 130GB partition to [swap]("https://help.ubuntu.com/community/SwapFaq#What is swap for?")?

post the output of:
```
df -h
```
and
```
free -m
```

---

### Post by gaalaaant on 2008-11-26
shoot I think I might have. Is that bad?

here are the results
df-h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  2.5G  6.9G  27% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  104K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  2.8M  946M   1% /dev
tmpfs                 948M  184K  948M   1% /dev/shm
lrm                   948M  2.0M  946M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda5             125G   59M  125G   1% /home
/dev/sda2              14G  8.0K   14G   1% /media/d_drive
daniel@daniel-laptop:~$ 

free -m:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  2.5G  6.9G  27% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  104K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  2.8M  946M   1% /dev
tmpfs                 948M  184K  948M   1% /dev/shm
lrm                   948M  2.0M  946M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda5             125G   59M  125G   1% /home
/dev/sda2              14G  8.0K   14G   1% /media/d_drive
daniel@daniel-laptop:~$

---

### Post by b0b138 on 2008-11-27
According to your results of df -h, your 125 gig partition (sda5) is already being mounted as /home.

---

### Post by gaalaaant on 2008-11-27
so if I were to save something in Windows, on that partition, it would appear on /home for Ubuntu?

---

### Post by nzadLithium on 2008-11-27
I could be entirely wrong with this answer as too many people are dumping their fdisk -l all over the place in this thread and i can't be bothered working out who's is who's. XD
Since its your /home though, i'm assuming that its formatted as either ext2 or ext3, as such, if you were to install software on windows that let it read and right those file systems then yes, but with a normal windows install it wouldn't recognise the drive so you wouldn't actually be able to read or write to it.

---

### Post by gaalaaant on 2008-11-27
thanks, but do you know the name of any such software? and would it take alot of setup?

---

### Post by nzadLithium on 2008-11-28
take a look here [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by gaalaaant on 2008-11-28
thanks guys, you've been a reall help despite my incompetence :)

---

