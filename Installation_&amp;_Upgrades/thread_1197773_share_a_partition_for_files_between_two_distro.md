---
title: "share a partition for files between two distro"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by JDPP on 2009-06-26
Hi, 

here is how my disk is partitionned (on a netbook) :
part 0 1 2 : windows xp, as pre installed I just reduce the third one to partition for linux
3 : 40 G free partitionned as ext3
4 and 5 : boot and swap for 64studio
6 and 7 : boot and swap for Ubuntu Studio.

My idea was sharing the part 3 to save some music file between the two linux.
But when I try to copy some files from Ubuntu Studio with nautilus, I don"t have the rights.
(the partition is mounted, with the lost and found folder).

I tried to launch nautilus from shell root, it launches but doesn't see the partition 3.

I assume I have something wrong, but I'm quite noob and didn't find out what.

I don't want to be able to swich "live" between the two distro, but I'd like to have a shared folder for the files I'll use with the distro I chose to boot.
(also, as I am testing distros, and need a few giga of mp3, I'd tought about a partition more to put those files in so as I don't have to copy them again each time I try a new distrib....)

thanks in advance

---

### Post by merlinus on 2009-06-26
Post results of:

```

sudo fdisk -l

```

---

### Post by JDPP on 2009-06-27
```
Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x971264c3

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1               1         510     4096543+  12  Compaq diagnostics
/dev/sda2   *         511        5610    40965750    7  HPFS/NTFS
/dev/sda3            5611        8366    22137570    7  HPFS/NTFS
/dev/sda4            8367       19457    89088457+   5  Etendue
/dev/sda5            8367       13375    40234761   83  Linux
/dev/sda6           13376       16286    23382576   83  Linux
/dev/sda7           16287       16418     1060258+  82  Linux swap / Solaris
/dev/sda8           16419       19325    23350446   83  Linux
/dev/sda9           19326       19457     1060258+  82  Linux swap / Solaris

```as I understand : 
sda1 is the XP recovery
sda2 is XP "c:"
sda3 is XP document
they are primary
sda4 is splitted into 5 logical partition
sda5 is the one i'd like to use with my two distros
6/7 is 64studio
8/9 is ubuntu studio

I tried those command line :
tune2fs -j /dev/sda5 && mount
tune2fs 1.41.4 (27-Jan-2009)
Le système de fichiers a déjà un journal.
sda5 has already a journal file...

mount /dev/sda5 /media/Zik
mount: le point de montage /media/Zik n'existe pas
mount point doesn't exist

sda5 is mounted as /media/zik in nautilus, but I can't copy file into the partition : error not allowed...

thx

---

### Post by kixome on 2009-06-27
show me the contents of your /etc/fstab from both distros
and the output of command: mount from both distros

---

### Post by JDPP on 2009-06-27
from ubuntu studio :
```
~# ls -l /etc/fstab
-rw-r--r-- 1 root root 753 2009-06-26 12:59 /etc/fstab
```

I can't see fstab directory thru nautilus either, (i checked show hidden files).
```

mount /dev/sda5 /media/Zik
mount: le point de montage /media/Zik n'existe pas
```
mount point doesn't exist

I'll try in the other in a few minutes

---

### Post by JDPP on 2009-06-27
```
root:~# ls -l /etc/fstab
-rw-r--r-- 1 root root 792 2009-06-26 05:50 /etc/fstab
root:~# mount /dev/sda5 /media/Zik
mount: /dev/sda5 already mounted or /media/Zik busy
mount: according to mtab, /dev/sda5 is already mounted on /media/Zik

```

I also tried to copy a file : permission denied
no /etc/fshare found by navigation..

---

### Post by kixome on 2009-06-27
i just wanted you to type mount, not try to mount the drive, as far as fstab use: sudo gedit /etc/fstab

---

### Post by JDPP on 2009-06-28
mount :

```
/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-3-rt/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/salsa404/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
```Sudo gedit fstab 
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=1e9d6528-98c0-4b81-8e9a-a0cc3da233fb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=27f9b856-eb0c-4065-b767-524ec47f6e74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by JDPP on 2009-06-28
from the other distro :
```
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /proc/bus/usb type usbfs (rw)

```

sudo gedit /etc/fstab 	

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=13be3d95-5f8b-48de-8325-e1ac6c604c3b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4b0a43d6-f3b9-44f2-8b68-f708704614b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs  defaults 0 0
```

---

### Post by ridgeland on 2009-06-28
Hi JDPP,
I've been using a shared Data partition for music and photos for years now.
I don't like and avoid UUID instead I only use /dev/sda5 etc.  I have about 20 partitions for Linux OS (two hard drives).  They all share a Data partition. In each in /etc/fstab is:
```
/dev/sda5		/Data			ext3	defaults	0 0
```
Each new Linux I install I use
```
$ sudo mkdir /Data
```
This has to be done before booting with the revised fstab.  You can manually test this by making /Data then using
```
$ sudo mount /dev/sda5 /Data
```
If you cannot read and write then change the permissions.
```
$ sudo chmod -R 777 /Data
```
One problem I encountered with all those distros is the default user is 500 on some 1000 on some.  To share data easily you need to always be the same user number, not just the same name.  The control is UID_MIN in /etc/login.defs
Just add the above line in /etc/fstab (you're using sda5 same as I do) make the directory /Data, mount it manually change permissions and test making files
```
$ touch /Data/testfile
$ ls /Data

```
One other note is you're wasting 1 GB having two swaps files but using them one at a time.  For all my Linux in /etc/fstab I use
```
/dev/sda1		/UserHome		ext2	defaults	0 0
# /dev/sda2 = SWAP space of 2 GB
/dev/sda2		none			swap	sw			0 0
```
In your case
/dev/sda7 could be used by both Linux by changing /etc/fstab in both to use /dev/sda7 rather than that UUID string.
I also use /UserHome for my PC's common files.  For example I share Firefox bookmarks between all the Linux using Firefox 3.0 by keeping the bookmarks in /UserHome and just using a link to it from all the Linux.  Here /Data is open to the local network (NFS) so my spouse can read/write to it, but /UserHome is not on the network.
Sorry to be long winded.  What you want to do is easy though.

---

### Post by JDPP on 2009-06-28
ridgeland, a BIG BIG thank you !  I did as you say, and it works for my ubuntu studio. ... (but i crashed trying to copy a few giga...) and for the other after reboot !  so once again MANY THANKS !!! When I'm a linux grown up I'll try the swap trick but I don't really need it now.  one more BIG thx !

---

### Post by JDPP on 2009-06-28
justone more question can I later move the zik folder from system file to another place ?

---

### Post by ridgeland on 2009-06-28
Great!
What is the zik folder?
My habit: I mount my partitions to /mnt/sda5, /mnt/sda6 ...
I mount my USB devices to /media/NikonD40, /media/CFReader ...
I'm not sure which you are doing or if your are trying to mount a sub-directory.
Sub-directory mounts require "bind". fstab assumes that you are mounting the entire partition to one point.  If you want to mount just partition/folder then you need bind.

---

### Post by JDPP on 2009-06-29
my Zik is your Data ;)

about moving :zik, the point is ix'd like to see it in the shortcuts (Media, File System, and user....), but I'll find out, have to learn by myself also

point is : i was stuck losing a lot of time and thank to you I can move ahead !!

---

### Post by ridgeland on 2009-06-29
Shortcuts?
If you open gedit or OpenOffice or something else then go File -> Open you get a list you can drill down and open files.  There you click once on Zik to highlight it then click on [Add] bottom left side of window.  Zik then shows up on the left side for faster selection.  That's what I did.  You will also find that doing that also added it to the main menu under "Places".

Suggestions for study:
man pages... 
try $ man fstab
There is a Google-Linux  To add Google Linux to search bar: go to [http://mycroft.mozdev.org/quick/google.html](http://mycroft.mozdev.org/quick/google.html) 
Mandriva forums is a good place to learn if you want a forum in French.  There are some differences like their control and settings tool, but things like fstab are the same in Ubuntu and Mandriva.

You've got the right attitude. Have fun!

---

### Post by JDPP on 2009-06-30
thx !

---

