---
title: "How to install (only) a kernel from an installation CD"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by tg1w on 2009-11-04
Hello

While trying to free up space it seems I managed to erase or linux-images (had 5-6 of them). When I restarted the computer... surprise, only Ubuntu memory test appears.

Using a installation CD, how may I install just the kernel, so that the rest of my system remains intact? I wouldn't want to install everything from scratch.

Thank you very much

---

### Post by tg1w on 2009-11-05
No advice out there? I'll end up erasing my previous system and installing Karmic from scratch...

Please, any advice. Thanks

---

### Post by bribera on 2009-11-05
This is definitely possible to do, but it'll be tricky. I'd advise following the install method that Gentoo uses: booting into a shell using the install disk, mounting the drive, and chrooting your environment into your old system. Then you can start some basic services (i.e. networking) and install the latest kernel using aptitude.

I'd basically do something like this:

```
# Boot into a ROOT shell from the installer - BE CAREFUL!
# Create a mount point for your existing system
mkdir /mnt/system
# Mount the root partition
# Note that my root filesystem is ext4 on /dev/sda2 - you need to adjust for yours
mount -t ext4 / /dev/sda2
# chroot into your old system
chroot /mnt/system /bin/bash
# update some environment variabls
env-update
source /etc/profile
# mount all of your previous mount points
mount -a
```

Then you should be able to start networking & find a kernel to install.

Let me know if you need more detail - I'd be happy to try to figure things out with you.

I'm using this document as a starting point:
[http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=6#doc_chap1](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=6#doc_chap1)

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> 
```
# Boot into a ROOT shell from the installer - BE CAREFUL!
# Create a mount point for your existing system
mkdir /mnt/system
# Mount the root partition
# Note that my root filesystem is ext4 on /dev/sda2 - you need to adjust for yours
[COLOR="Red"]mount -t ext4 / /dev/sda2[/COLOR]


Hi. Thank you for your help. For my computer I am using [CODE]mount -t ext3 / /dev/sda2
``` but it is not working. I get the following output: 

```
ubuntu@ubuntu:~$ sudo mount -t ext3 / /dev/sda2
mount: / is not a block device

```

I'm running Ubuntu from the install disc. fdisk outputs the following:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  83  Linux
/dev/sda2   *        3531        6209    21519067+   7  HPFS/NTFS
/dev/sda3            6210       14593    67344480    7  HPFS/NTFS
/dev/sda4             915        1845     7478257+   5  Extended
/dev/sda5             915        1036      979933+  83  Linux
/dev/sda6            1037        1650     4931923+  83  Linux
/dev/sda7            1651        1845     1566306   82  Linux swap / Solaris

```

Thank you very much for your help and hope to get this cracking soo.

---

### Post by bribera on 2009-11-06
Oh, oops -- it looks like I reversed the parameters. The device needs to come first, and then the directory you'd like to mount. I also accidentally told you to mount it to / -- that doesn't work, since you can't mount to / directly. You have to mount to a different directory and chroot into it.

There's another problem with the command you're running:
You're mounting /dev/sda2, which looks like a Windows partition to me - it's of type HPFS/NTFS.

Do you know which of your partitions is actually the root partition for Linux? My guess is it's /dev/sda1 or /dev/sda6, since they're the largest Linux partitions... but you seem to have a weird partition scheme.

You need to figure out which one is actually supposed to be mounted as / - you can do this by trial and error.

```

# First you'll make a mount point:
ubuntu@ubuntu:~$ sudo mkdir /mnt/system

# Then you'll mount one of the Linux partitions:
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/system

# Then check to see if it's actually the / partition:
ubuntu@ubuntu:~$ ls /mnt/system

# If you decide it's not the / partition, unmount it before trying a new one:
ubuntu@ubuntu:~$ sudo umount /mnt/system
```

An example of what ls might output is this, from my / partition:
```

total 100K
drwxr-xr-x   2 root root 4.0K 2009-10-26 11:47 bin
drwxr-xr-x   3 root root 4.0K 2009-10-27 11:33 boot
lrwxrwxrwx   1 root root   11 2009-10-02 11:15 cdrom -> media/cdrom
drwxr-xr-x  17 root root 4.0K 2009-11-06 10:38 dev
drwxr-xr-x 146 root root  12K 2009-11-06 10:38 etc
drwxr-xr-x   3 root root 4.0K 2009-10-02 11:28 home
lrwxrwxrwx   1 root root   33 2009-10-19 11:22 initrd.img -> boot/initrd.img-2.6.31-14-generic
lrwxrwxrwx   1 root root   33 2009-10-09 18:08 initrd.img.old -> boot/initrd.img-2.6.31-13-generic
drwxr-xr-x  13 root root  12K 2009-10-27 12:44 lib
drwxr-xr-x   7 root root  12K 2009-10-26 11:47 lib32
lrwxrwxrwx   1 root root    4 2009-10-02 11:16 lib64 -> /lib
drwx------   2 root root  16K 2009-10-02 11:15 lost+found
drwxr-xr-x   3 root root 4.0K 2009-09-29 13:01 media
drwxr-xr-x   2 root root 4.0K 2009-07-13 19:36 mnt
drwxr-xr-x   3 root root 4.0K 2009-10-12 13:48 opt
dr-xr-xr-x 202 root root    0 2009-11-06 10:36 proc
drwx------  14 root root 4.0K 2009-10-29 12:39 root
drwxr-xr-x   2 root root 4.0K 2009-10-27 11:32 sbin
drwxr-xr-x   2 root root 4.0K 2009-08-25 04:07 selinux
drwxr-xr-x   3 root root 4.0K 2009-10-07 12:00 srv
drwxr-xr-x  13 root root    0 2009-11-06 10:36 sys
drwxrwxrwt  14 root root  340 2009-11-06 11:13 tmp
drwxr-xr-x  12 root root 4.0K 2009-10-30 11:34 usr
drwxr-xr-x  15 root root 4.0K 2009-09-29 13:12 var
lrwxrwxrwx   1 root root   30 2009-10-19 11:22 vmlinuz -> boot/vmlinuz-2.6.31-14-generic
lrwxrwxrwx   1 root root   30 2009-10-09 18:08 vmlinuz.old -> boot/vmlinuz-2.6.31-13-generic

```

Your partitioning scheme is a little complicated, so you may need to check several of your partitions. Just mount and ls each in order, umounting if you decide you've chosen the wrong one.

Once you get a partition with directories reasonably similar to the ones I posted, you can move into that directory and chroot:

```
# chroot into your old system
ubuntu@ubuntu:~$ sudo chroot /mnt/system /bin/bash

# update some environment variables
ubuntu@ubuntu:~$ env-update
ubuntu@ubuntu:~$ source /etc/profile

# mount all of your previous mount points from /etc/fstab
ubuntu@ubuntu:~$ sudo mount -a
```

---

### Post by tg1w on 2009-11-06
Ok. So I got past the mounting and the /bin/bash parts (I mounted sda1).
Right now I get the following errors:

```
root@ubuntu:/# env-update
bash: env-update: command not found

```

```

root@ubuntu:/# source /etc/profile
root@ubuntu:/# mount -a
mount: special device /dev/disk/by-uuid/9c30c2b1-7423-48c7-86c5-eceddd6d41f6 does not exist
ntfs-3g: Failed to access volume '/dev/sda3': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

Work under way.

---

### Post by bribera on 2009-11-06
The env-update error doesn't matter; I guess that's a Gentoo-only thing.

What does the following output?
```
ubuntu@ubuntu:~$ mount -l
```

Also, can you post the output of:
```
ubuntu@ubuntu:~$ cat /etc/fstab
```

---

### Post by tg1w on 2009-11-06
I have also tried to install directly through apt-get a linux-image, but:

```
root@ubuntu:/# sudo apt-get install linux-image-2.6.30
sudo: unable to resolve host ubuntu
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), 
is another process using it?

```

No chance to get that working :).

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> The env-update error doesn't matter; I guess that's a Gentoo-only thing.

What does the following output?
```
ubuntu@ubuntu:~$ mount -l
```

Also, can you post the output of:
```
ubuntu@ubuntu:~$ cat /etc/fstab
```

Thank you Bribera. I get the following output:

```

root@ubuntu:/# mount -l
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=c1448a6e-04eb-46a1-80f0-5154db00f923 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=9c30c2b1-7423-48c7-86c5-eceddd6d41f6 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=ca1de354-fe68-4bb4-8258-29481db9f3e5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Media ntfs-3g defaults,locale=en_GB.UTF-8 0 0
#/dev/sda2 /media/Windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0

```

By the way, my partitioning is indeed strange. Dual boot basically, the linux root, home, swap, the Windows and some other partitions. Cheers

---

### Post by bribera on 2009-11-06
Hmm... two thoughts on that:

[LIST=1]
[*]Your networking probably isn't running, so you won't be able to download stuff
[*]/var might be mounted elsewhere (!?)
[/LIST]

For the first, try running this:
```
ubuntu@ubuntu:~$ sudo /etc/init.d/networking start
```

For the second, post your mount -l and /etc/fstab. It could be that one of your other partitions needs to be mounted in order to access /var.

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> Hmm... two thoughts on that:

[LIST=1]
[*]Your networking probably isn't running, so you won't be able to download stuff
[*]/var might be mounted elsewhere (!?)
[/LIST]

For the first, try running this:
```
ubuntu@ubuntu:~$ sudo /etc/init.d/networking start
```

For the second, post your mount -l and /etc/fstab. It could be that one of your other partitions needs to be mounted in order to access /var.

Hmm. I have only /home located on a different partition. The rest of the filesystem is on sda1.

```

root@ubuntu:/# sudo /etc/init.d/networking start
sudo: unable to resolve host ubuntu

```

Will try to do things all over again, maybe I missed something.

---

### Post by tg1w on 2009-11-06
I commented the /sda3 part of /etc/fstab. Still get a 
```
root@ubuntu:/# mount -a
mount: special device /dev/disk/by-uuid/9c30c2b1-7423-48c7-86c5-eceddd6d41f6 does not exist

```
which I don't know where it comes from

---

### Post by tg1w on 2009-11-06
> **tg1w said:**
> I commented the /sda3 part of /etc/fstab. Still get a 
```
root@ubuntu:/# mount -a
mount: special device /dev/disk/by-uuid/9c30c2b1-7423-48c7-86c5-eceddd6d41f6 does not exist

```
which I don't know where it comes from

Anyone with an idea about the above? What does "special device" mean... it's not in /etc/fstab.

Thanks

---

### Post by bribera on 2009-11-06
It actually is in /etc/fstab - looks like it's your /dev/sda6 device's UUID.

What does mount with the -l flag output?

```
root@ubuntu:/# mount **-l**
```

That will show currently mounted devices. Not having a /home could be screwing things up.

---

### Post by tg1w on 2009-11-06
As far as I can see, there is a */dev/disk/by-uuid/9c30...f6* entry. I deleted it but I get the same error.

There is something interesting here:

```

ubuntu@ubuntu:/$ sudo chroot /mnt/system /bin/bashroot@ubuntu:/# cd /dev/
root@ubuntu:/dev# ls
agpgart   dsp2	 i2c-7	midi0	mixer3	    ram11  ram7       smpte1   tty3
apm_bios  dsp3	 kmem	midi00	mpu401data  ram12  ram8       smpte2   tty4
audio	  fd	 loop0	midi01	mpu401stat  ram13  ram9       smpte3   tty5
audio1	  full	 loop1	midi02	null	    ram14  random     sndstat  tty6
audio2	  i2c-0  loop2	midi03	port	    ram15  rmidi0     stderr   tty7
audio3	  i2c-1  loop3	midi1	ptmx	    ram16  rmidi1     stdin    tty8
audioctl  i2c-2  loop4	midi2	pts	    ram2   rmidi2     stdout   tty9
console   i2c-3  loop5	midi3	ram	    ram3   rmidi3     tty      urandom
core	  i2c-4  loop6	mixer	ram0	    ram4   sequencer  tty0     xconsole
dsp	  i2c-5  loop7	mixer1	ram1	    ram5   shm	      tty1     zero
dsp1	  i2c-6  mem	mixer2	ram10	    ram6   smpte0     tty2

```

then

```

root@ubuntu:/dev# exit
exit
ubuntu@ubuntu:/$ cd /dev/disk/by-uuid/
ubuntu@ubuntu:/dev/disk/by-uuid$ ls
3B9630BF428D460C  c1448a6e-04eb-46a1-80f0-5154db00f923
5AB5-4E84         ca1de354-fe68-4bb4-8258-29481db9f3e5
AEA23EEAA23EB6A5

```

Where is the error coming from... I don't know now. That file doesn't even exist any more. 

```
root@ubuntu:/# sudo mount -a
sudo: unable to resolve host ubuntu
mount: special device /dev/disk/by-uuid/9c30c2b1-7423-48c7-86c5-eceddd6d41f6 does not exist

```

---

### Post by tg1w on 2009-11-06
Networking is not working...and not willing to work.

```

ubuntu@ubuntu:/$ sudo chroot /mnt/system /bin/bash
root@ubuntu:/# service networking start
root@ubuntu:/# sudo apt-get install linux-image
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-regex1.34.1 ...
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.28-16-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-image linux-image-2.6.28-16-generic ...
0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
Need to get 24.7MB of archives.
After this operation, 96.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://gb.archive.ubuntu.com jaunty-updates/main 
linux-image-2.6.28-16-generic 2.6.28-16.55
  Could not resolve 'gb.archive.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main 
linux-image-2.6.28-16-generic 2.6.28-16.55
...
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

root@ubuntu:/# sudo /etc/init.d/networking start
sudo: unable to resolve host ubuntu

```

---

### Post by bribera on 2009-11-06
You just need to mount it using the device name instead of the UUID. The UUID isn't working because you didn't go through the normal bootup procedure, so it isn't set up.

Try this:
```
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda6 /home
```

Your "sudo: unable to resolve host ubuntu" error has to do with your hostname, I believe.

Try doing this:
```
ubuntu@ubuntu:/$ cat /etc/hostname
ubuntu@ubuntu:/$ sudo hostname ##### whatever the second entry for 127.0.0.1 is
```

In other words, your host name is currently set to "ubuntu", but /etc/hosts is expecting a different name. My computer has the following entries:
```
127.0.0.1	localhost
127.0.1.1	scylla
```

So I'd do:

```
ubuntu@ubuntu:/$ sudo hostname scylla
```

Then check whether you're connected to the internet:
```
ubuntu@ubuntu:/$ ping -c 3 google.com
```

---

### Post by tg1w on 2009-11-06
I will try to install the linux-image from the Ubuntu CD. If anyone can provide help, it will be highly appreciated.

Thank you very much all.

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> It actually is in /etc/fstab - looks like it's your /dev/sda6 device's UUID.

What does mount with the -l flag output?

```
root@ubuntu:/# mount **-l**
```

That will show currently mounted devices. Not having a /home could be screwing things up.

Indeed, I missed that. It is the /home partition. mount -l doesn't show /home as it is not mounted.

```

ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda6 /mnt/system/home
ubuntu@ubuntu:/$ cd mnt/system/home
ubuntu@ubuntu:/mnt/system/home$ ls
lost+found  x  y

```
(x and y are the two usernames)

```
ubuntu@ubuntu:/$ sudo chroot /mnt/system /bin/bash
root@ubuntu:/# mount -a
mount: special device /dev/disk/by-uuid/9c30c2b1-7423-48c7-86c5-eceddd6d41f6 does not exist
```

---

### Post by bribera on 2009-11-06
Yeah, mount -a won't work in this situation. I think it's because your real UUIDs are in the *livecd's* /dev, but you've chrooted into another /dev. It doesn't matter, now that you've mounted your home directory as well.

Just out of curiosity, can you start your window manager? I.e.

```
root@ubuntu:/# /etc/init.d/gdm start
```

If so, you can probably add your CD as an apt source and install a kernel from there. That's assuming you still can't get networking started...

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> You just need to mount it using the device name instead of the UUID. The UUID isn't working because you didn't go through the normal bootup procedure, so it isn't set up.

Try this:
```
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda6 /home
```

Your "sudo: unable to resolve host ubuntu" error has to do with your hostname, I believe.

Try doing this:
```
ubuntu@ubuntu:/$ cat /etc/hostname
ubuntu@ubuntu:/$ sudo hostname ##### whatever the second entry for 127.0.0.1 is
```

In other words, your host name is currently set to "ubuntu", but /etc/hosts is expecting a different name. My computer has the following entries:
```
127.0.0.1	localhost
127.0.1.1	scylla
```

So I'd do:

```
ubuntu@ubuntu:/$ sudo hostname scylla
```

Then check whether you're connected to the internet:
```
ubuntu@ubuntu:/$ ping -c 3 google.com
```

Thank you Bribera. I did everything all over again (the more times, the better). Indeed, root@ubuntu had ubuntu as hostname, while /etc/hosts had something else (x). I run *sudo hostname x* but internet is not working. 
*sudo /etc/init.d/networking start* similarly doesn't help.

At this point I have to say that I have commented out the /etc/fstab line where the /home was mounted. Consequently:

```

root@ubuntu:/# mount -a
root@ubuntu:/# mount -l
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

```
/etc/init.d/gdm start
``` has equally no effect.

---

### Post by bribera on 2009-11-06
Do you use Wifi, or a cable for your internet connection?

What does this command output?
```
ubuntu@ubuntu:~$ grep cdrom /etc/apt/sources.list
```

If there is a cdrom line in your sources.list, you can probably uncomment it and install packages from the CD.

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> Do you use Wifi, or a cable for your internet connection?

What does this command output?
```
ubuntu@ubuntu:~$ grep cdrom /etc/apt/sources.list
```

If there is a cdrom line in your sources.list, you can probably uncomment it and install packages from the CD.

Hi. I use Wifi. This is grep's output:
```
root@ubuntu:/# grep cdrom /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ 
intrepid main restricted

```

---

### Post by bribera on 2009-11-06
> **tg1w said:**
> Hi. I use Wifi.
Ah, that makes sense then. You'd have to use iwconfig to get on the network, and that's a pain.

Try this:
[LIST=1]
[*]Make a backup copy of /etc/apt/sources.list
[*]Edit /etc/apt/sources.list and remove everything except that cdrom line
[*]Make sure the cdrom line is uncommented
[/LIST]

Then do:
```
sudo apt-get update
```

And see if you can install a kernel.

If that works **remember to**:
[LIST=1]
[*]Uncomment the line about mounting /home in /etc/fstab - *VERY IMPORTANT*
[*]Replace your edited /etc/apt/sources.list with your backup copy
[/LIST]

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> Ah, that makes sense then. You'd have to use iwconfig to get on the network, and that's a pain.

Try this:
[LIST=1]
[*]Make a backup copy of /etc/apt/sources.list
[*]Edit /etc/apt/sources.list and remove everything except that cdrom line
[*]Make sure the cdrom line is uncommented
[/LIST]

Then do:
```
sudo apt-get update
```

And see if you can install a kernel.

If that works **remember to**:
[LIST=1]
[*]Uncomment the line about mounting /home in /etc/fstab - *VERY IMPORTANT*
[*]Replace your edited /etc/apt/sources.list with your backup copy
[/LIST]

Thank you. 

I had already been trying to trick Synaptic into using only the CD-ROM. To start with, this was mounted before chroot-ing, through a 
```

sudo mkdir /mnt/system/media/cdrom0
sudo mount /dev/scd0 /mnt/system/media/cdrom0

```

All perfect. After chroot-ing I was able to start Synaptic. Final problem now is that when I'm looking for linux-image packages, I don't find one any more. I have a set of linux-image-2.6.*-generic.

If I try to mark one for installation, I get something like:
[I]linux-image-2.6.28-15-generic:

Package linux-image-2.6.28-15-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
[/I]

---

### Post by tg1w on 2009-11-06
Yeap, life is not great.

Only a couple of packages seem to be available in Synaptic. I tried to install a "lupin-support", the cdrom started spinning, package was downloaded. Then came a [COLOR="Red"]Error failed to fork pty[/COLOR] error message.

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> Ah, that makes sense then. You'd have to use iwconfig to get on the network, and that's a pain.

Try this:
[LIST=1]
[*]Make a backup copy of /etc/apt/sources.list
[*]Edit /etc/apt/sources.list and remove everything except that cdrom line
[*]Make sure the cdrom line is uncommented
[/LIST]

Then do:
```
sudo apt-get update
```

And see if you can install a kernel.

If that works **remember to**:
[LIST=1]
[*]Uncomment the line about mounting /home in /etc/fstab - *VERY IMPORTANT*
[*]Replace your edited /etc/apt/sources.list with your backup copy
[/LIST]


```

root@teodor-d630:/# sudo aptitude update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Reading package lists... Done

root@teodor-d630:/# sudo aptitude search linux
i   libselinux1                                                   - SELinux shared libraries                                               
v   linux-boot-loader                                             -                                                                        
i   linux-firmware                                                - Firmware for Linux kernel drivers                                      
v   linux-headers                                                 -                                                                        
v   linux-headers-2.6                                             -                                                                        
i A linux-headers-2.6.28-11                                       - Header files related to Linux kernel version 2.6.28                    
i A linux-headers-2.6.28-11-generic                               - Linux kernel headers for version 2.6.28 on x86/x86_64                  
i   linux-headers-2.6.28-13                                       - Header files related to Linux kernel version 2.6.28                    
i   linux-headers-2.6.28-13-generic                               - Linux kernel headers for version 2.6.28 on x86/x86_64                  
i   linux-headers-2.6.28-14                                       - Header files related to Linux kernel version 2.6.28                    
i   linux-headers-2.6.28-14-generic                               - Linux kernel headers for version 2.6.28 on x86/x86_64                  
i   linux-headers-2.6.28-15                                       - Header files related to Linux kernel version 2.6.28                    
i   linux-headers-2.6.28-15-generic                               - Linux kernel headers for version 2.6.28 on x86/x86_64                  
i   linux-headers-2.6.28-16                                       - Header files related to Linux kernel version 2.6.28                    
i   linux-headers-2.6.28-16-generic                               - Linux kernel headers for version 2.6.28 on x86/x86_64                  
i   linux-headers-generic                                         - Generic Linux kernel headers                                           
v   linux-image                                                   -                                                                        
v   linux-image-2.6                                               -                                                                        
c   linux-image-2.6.27-11-generic                                 - Linux kernel image for version 2.6.27 on x86/x86_64                    
c   linux-image-2.6.27-7-generic                                  - Linux kernel image for version 2.6.27 on x86/x86_64         

```

---

### Post by bribera on 2009-11-06
> **tg1w said:**
> Final problem now is that when I'm looking for linux-image packages, I don't find one any more. I have a set of linux-image-2.6.*-generic.

If I try to mark one for installation, I get something like:
[I]linux-image-2.6.28-15-generic:

Package linux-image-2.6.28-15-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

Hmm. Did you update your package lists before trying that? You probably did... I just want to cover all of the bases.

---

### Post by tg1w on 2009-11-06
> **bribera said:**
> Hmm. Did you update your package lists before trying that? You probably did... I just want to cover all of the bases.

Yes, I performed the update (there is a sudo aptitude update in a previous post). ... This should be a basic operation though...

---

### Post by bribera on 2009-11-06
Ah sorry, I missed that. It could be that the cdrom doesn't actually contain an installable kernel package, since it copies over a base system. I'm really shooting in the dark with that explanation.

I'd revert to your original /etc/apt/sources.list and make your goal to get on the internet.

You **should** be able to plug in a networking cable and get online. If that's an option, I'd try it.

You'd plug it in and do something like:
```
sudo ifup eth0
sudo dhclient eth0
```

Then test to see if you're online:
```
ping -c 3 google.com
```

You really should be able to get online, and once you're online you should be able to install a kernel. :-|

---

### Post by tg1w on 2009-11-07
> **bribera said:**
> Ah sorry, I missed that. It could be that the cdrom doesn't actually contain an installable kernel package, since it copies over a base system. I'm really shooting in the dark with that explanation.

I'd revert to your original /etc/apt/sources.list and make your goal to get on the internet.

You **should** be able to plug in a networking cable and get online. If that's an option, I'd try it.

You'd plug it in and do something like:
```
sudo ifup eth0
sudo dhclient eth0
```

Then test to see if you're online:
```
ping -c 3 google.com
```

You really should be able to get online, and once you're online you should be able to install a kernel. :-|

Thank you Bribera. I will be working on that. Current results are:

```
ubuntu@ubuntu:~$ sudo chroot /mnt/system /bin/bash
root@ubuntu:/# sudo ifup eth0
sudo: unable to resolve host ubuntu
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
root@ubuntu:/# sudo hostname x
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo hostname x
root@ubuntu:/# hostname
x
root@ubuntu:/# sudo ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

root@ubuntu:/# sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

/proc/net/dev: No such file or directory

root@ubuntu:/# ping -c 3 google.com
ping: unknown host google.com

```

---

### Post by tg1w on 2009-11-07
Hi. I managed to get the network started by copying the required files from the livecd filesystem. Started synaptic and downloaded a linux-image (needed wireless-crda too, among others) but I get the same [COLOR="Red"]Error failed to fork pty[/COLOR] when synaptic tries to install the packages... what a pity.

This is the output:
```
# synaptic
vte_terminal_forkpty() failed. Bad file descriptor
```

---

### Post by bribera on 2009-11-09
Gack, what an annoyance :( At least you got networking up :)

You can try to install it with dpkg instead of syntaptic, although who knows whether it'll actually install given that syntaptic is broken. To do that, try these instructions:

First, figure out what kernel version you're running:
```
uname -r
```

Based on that, choose the the directory containing your Ubuntu kernel from kernel.ubuntu.com: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) - also be sure to choose the correct architecture.

Install like this (my example is using [the 2.6.31.5 build]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/") for x86_64):
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-headers-2.6.31-02063105_2.6.31-02063105_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-headers-2.6.31-02063105-generic_2.6.31-02063105_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-image-2.6.31-02063105-generic_2.6.31-02063105_amd64.deb
sudo dpkg -i linux-headers-2.6.31-02063105_2.6.31-02063105_all.deb
sudo dpkg -i linux-headers-2.6.31-02063105-generic_2.6.31-02063105_amd64.deb
sudo dpkg -i linux-image-2.6.31-02063105-generic_2.6.31-02063105_amd64.deb
```

The other option you have is to install the kernel yourself. This basically means doing some of the work that syntaptic does for you:
[LIST]
[*]copying the right files into /boot
[*]updating grub to recognize the kernel
[*]hoping it works :|
[/LIST]

We can try that path if installing the .debs doesn't work...

---

### Post by tg1w on 2009-11-11
> **bribera said:**
> Gack, what an annoyance :( At least you got networking up :)

You can try to install it with dpkg instead of syntaptic, although who knows whether it'll actually install given that syntaptic is broken. To do that, try these instructions:

First, figure out what kernel version you're running:
```
uname -r
```

You mean the version of kernel I was previously running, or the one on the LiveCD?

The LiveCD is running version 2.6.31-14-generic. This however cannot be found on kernel.ubuntu.com. I have thus used simply v2.6.31.

```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/linux-headers-2.6.31-020631-generic_2.6.31-020631_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/linux-headers-2.6.31-020631_2.6.31-020631_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/linux-image-2.6.31-020631-generic_2.6.31-020631_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/linux-source-2.6.31_2.6.31-020631_all.deb

```

In order to install the above, I had to copy the /proc/bus/pci directory from the LiveCD filesystem. In order to install linux-image I was required to install wireless-crda, which can be obtained through
```
wget http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_i386.deb
sudo dpkg -i wireless-crda_1.7_i386.deb
```

This is the big output:
```

root@ubuntu:/# sudo dpkg -i linux-image-2.6.31-020631-generic_2.6.31-020631_i386.deb 
(Reading database ... 304651 files and directories currently installed.)
Preparing to replace linux-image-2.6.31-020631-generic 2.6.31-020631 (using linux-image-2.6.31-020631-generic_2.6.31-020631_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.31-020631-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=c1448a6e-04eb-46a1-80f0-5154db00f923'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-020631-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.31-020631-generic (2.6.31-020631) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-020631-generic
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=c1448a6e-04eb-46a1-80f0-5154db00f923'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-020631-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

```

---

### Post by tg1w on 2009-11-11
On restart, GRUB shows me the new 2.6.31 kernel, but the booting procedure stops midway - screen turns black.

I'll try to install the Jaunty kernel, 2.6.28.

---

### Post by tg1w on 2009-11-11
God bless you bribera.

After installing the 2.6.28 kernel and reverting to my very first /etc/fstab, the system correctly booted. That's where I'm writing from.

Issue solved. I'm very grateful. 

Regards

---

### Post by bribera on 2009-11-11
Awesome! Glad one of these crazy ideas finally panned out. :p

---

