---
title: "NTFS Mounting Problems -_-"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by Meshuggah27 on 2007-02-09
Im having alot of trouble mounting my 2 IDE NTFS Hard drives.

One is a 320gb Western Digital,  And the other is a 250gb Seagate barracuda both NTFS.

I have NO IDEA how to mount them and have been through many guides and have just sat there clueless on what to do.

My linux installation is on a seperate 20gb Western digital HDD.  All these drives are IDE btw.

Here is what it gives me when i type 'mount' in the terminal
> /dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/ipod type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)


And here is my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=c78e12ed-df98-4c15-848a-c3cdf51dd2e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a3b3a39e-c807-439d-99ec-6250ceba6535 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Also,
The 20gb Linux Installation HDD is /dev/hdb
The 250gb Seagate is /dev/hdd1
The 320gb WD HDD is /dev/hdc1

Hope ive provided as much information as needed for you guys to help! :(

---

### Post by taurus on 2007-02-09
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/hdc1   /media/hdc1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdd1   /media/hdd1   ntfs   nls=utf8,umask=0222   0   0

```
Save it.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hdc1 /media/hdd1
sudo mount -a
df -h
```

---

### Post by Meshuggah27 on 2007-02-09
O_O..............
I think i love you

Thank you so much my friend.  I wish i could repay you somehow.

---

### Post by taurus on 2007-02-09
> **Meshuggah27 said:**
> O_O..............
I think i love you

Easy there, tiger...  :lolflag:

---

### Post by ndefontenay on 2007-02-09
If you don't want to hit the command line, you can go to your system administration screen.

Choose the advanced button. 
You'll have to provide your password to be able to get there.
Select the hard disk icon (Must be the 1st icon on top).
Your hard disk might be detected but not enabled yet.
Selcet "Modify"

In the modify screen, choose the type of hardware: Select NTFS in the list.

after that I had a lot of trouble reading or writing. To solved it I had to choose my user as the owner.

You'll have to choose a mount point too. I choosed /media/windows
Save your modification and enable your hardware (You'll see it at the bottom near the modify button).

I guess a few print screens explains more. I'll come back with that later.

I've tried this yesterday without one single command line and I could reach my hard disk happily.

---

### Post by Meshuggah27 on 2007-02-09
Its cool dude,  Taurus solved the problem for me and it works great.  Just cached my 44gb of music and im blaring it with XMMS right now.

This forum is the freakin greatest for n00bs like me :D

Now if i could only get beryl to work,  Id consider Ubuntu my new operating system for life.

---

