---
title: "Won't let me use /home partition"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Mewshi on 2009-03-01
Hi!

Re-installing Intrepid on my girlfriend's computer (it's... screwed).

Problem is, it won't let me use her home directory partition as a mount point unless I format it again (NOT an option).

It's XFS.

I've had this same setup on my laptop for quite a while, and I never had this problem.  What's wrong with it? :(

Edit:  Great, it's not even showing up in nautilus now...  HELP!!!

---

### Post by Mewshi on 2009-03-01
anyone?

---

### Post by taurus on 2009-03-01
Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Mewshi on 2009-03-01
Remember, this is from the Install disc...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14ba14ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7476    60050938+  83  Linux

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4734        4982     2000092+  82  Linux swap / Solaris
/dev/sdb2               1        4733    38017791   83  Linux

Partition table entries are not in disk order

```
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="a5202e3e-bcff-4c36-dc9d-628457a84682" TYPE="xfs" 
/dev/sdb1: UUID="870ce337-f75b-4525-bdcd-c1431e896385" TYPE="swap" 
/dev/sdb2: UUID="db6e6dc9-bf78-4fb9-a365-50a4e463c787" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

```

```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb1 swap swap defaults 0 0

```

```
tmpfs                 378M  2.0M  376M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 378M  2.0M  376M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  100K  378M   1% /var/run
varlock               378M  4.0K  378M   1% /var/lock
udev                  378M  2.8M  376M   1% /dev
tmpfs                 378M  612K  378M   1% /dev/shm
rootfs                378M   76M  303M  20% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 378M   48K  378M   1% /tmp
/dev/sdb2              36G  4.8G   30G  15% /media/disk

```

---

### Post by Mewshi on 2009-03-01
what now?:confused:

---

### Post by Mewshi on 2009-03-01
Someone?

---

### Post by taurus on 2009-03-01
Did you install Ubuntu on /dev/sdb2 since it's ext3 (while you want to mount /dev/sda1--xfs filesystem)?

```
cat /media/disk/etc/fstab
```

---

### Post by Mewshi on 2009-03-01
```
ubuntu@ubuntu:~$ cat /media/disk/etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sdb2

UUID=db6e6dc9-bf78-4fb9-a365-50a4e463c787 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda1

UUID=a1202e3e-b4c9-4c36-9c99-628455a84682 /home           xfs     relatime        0       2

# /dev/sdb1

UUID=870ce337-f75b-4525-bdcd-c1431e896385 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by taurus on 2009-03-01
> **Mewshi said:**
> 
```

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="**[COLOR="Red"]a5202e3e-bcff-4c36-dc9d-628457a84682[/COLOR]**" TYPE="xfs" 
/dev/sdb1: UUID="870ce337-f75b-4525-bdcd-c1431e896385" TYPE="swap" 
/dev/sdb2: UUID="db6e6dc9-bf78-4fb9-a365-50a4e463c787" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

```

```
ubuntu@ubuntu:~$ cat /media/disk/etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sdb2

UUID=db6e6dc9-bf78-4fb9-a365-50a4e463c787 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda1

UUID=**[COLOR="Red"]a1202e3e-b4c9-4c36-9c99-628455a84682[/COLOR]** /home           xfs     relatime        0       2

# /dev/sdb1

UUID=870ce337-f75b-4525-bdcd-c1431e896385 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

As you can see, the UUID for /dev/sda1 is mis-matched.  Therefore, you need to edit /etc/fstab (on your harddrive)

```
gksudo gedit /media/disk/etc/fstab
```
and replace the old UUID with the right one.

```

UUID=a5202e3e-bcff-4c36-dc9d-628457a84682   /home    xfs   relatime    0   2
```
Save it and reboot without the LiveCD.

Assuming your login name is the same on /dev/sda1; otherwise, you would have a problem login in since you are now using /home from /dev/sda1, not /dev/sdb2.

---

### Post by Mewshi on 2009-03-01
This is from the install disc; re-installing due to (i believe) unrelated issues.  Upgrade gone awry, as it were...

---

### Post by Mewshi on 2009-03-01
Anyone know what I should have her do?

---

### Post by Mewshi on 2009-03-02
Can anyone help?

---

### Post by Mewshi on 2009-03-02
```
* ERROR: mismatched uuid in log
*            SB : a5202e3e-bcff-4c36-dc9d-628457a84682
*            log: a1202e3e-b4c9-4c36-9c99-628455a84682
disconnected inode 129, nlink 1
disconnected inode 130, nlink 1
sb_icount 0, counted 33152
sb_ifree 0, counted 883
sb_fdblocks 15005388, counted 7122393
sb_features2 (0x8) not same as sb_bad_features2 (0x80008)

```

---

### Post by Mewshi on 2009-03-02
Help!

---

### Post by taurus on 2009-03-02
You still can't mount /dev/sda1 to /home?  

Edit /etc/fstab and replace the line for /dev/sda1 to this.

```

/dev/sda1    /home    xfs     defaults     0    2
```
Save it and reboot.

---

### Post by Mewshi on 2009-03-02
It seems to be a problem with XFS itself... :\

No clue how to fix it... :(

---

### Post by taurus on 2009-03-02
Okay, where does it mount to now?

```
df -h
```

---

### Post by Mewshi on 2009-03-02
It doesn't mount because there's a problem with XFS! -_-

How do I fix XFS?
I ran xfs_repair, and it's not going...

What now?

---

### Post by taurus on 2009-03-02
When you said "it's not going," what exactly was wrong with it?

[http://linux.die.net/man/8/xfs_repair](http://linux.die.net/man/8/xfs_repair)

Other thing you can do is to use TestDisk to fix your /dev/sda1.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mewshi on 2009-03-02
verified secondary superblock...
writing modified primary superblock

fatal error -- primary superblock write failed!


Error it gives

---

### Post by Mewshi on 2009-03-03
Hello...?

---

### Post by Mewshi on 2009-03-04
Anyone at all?

---

