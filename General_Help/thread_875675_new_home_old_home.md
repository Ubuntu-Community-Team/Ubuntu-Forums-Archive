---
title: "new home old home"
date: 2008-07-31
forum: General Help
---

### Post by philetus on 2008-07-31
I'm using a live disk to create a home.I've gotten this far:

:/mnt/oldhome$ sudo find . -depth -print0 | sudo cpio --null --sparse --preserve-modification-time -pvd /mnt/newhome

I get this: 0 blocks and no files are copied to newhome.

Here is everything in terminal:

ubuntu@ubuntu:~$ sudo mkdir /mnt/newhome
ubuntu@ubuntu:~$ sudo mount -t ext3/dev/hda3 /mnt/newhome
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$  sudo mount -t ext3/dev/hda3/mnt/newhome
ubuntu@ubuntu:~$ sudo mkdir /mnt/oldhome
ubuntu@ubuntu:~$ sudo mount -t ext3/dev
ubuntu@ubuntu:~$ hda1 /mnt/oldhome
bash: hda1: command not found
ubuntu@ubuntu:~$ cd /oldhome
bash: cd: /oldhome: No such file or directory
ubuntu@ubuntu:~$ cd /mnt/oldhome
ubuntu@ubuntu:/mnt/oldhome$ sudo find . -depth -print0 | sudo cpio --null --sparse --preserve-modification-time -pvd mnt/newhome
0 blocks
ubuntu@ubuntu:/mnt/oldhome$ sudo find . -depth -print0 | sudo cpio --null --sparse --preserve-modification-time -pvd mnt/newhome/
0 blocks
ubuntu@ubuntu:/mnt/oldhome$ sudo find . -depth -print0 | sudo cpio --null --sparse --preserve-modification-time -pvd / mnt/newhome/
cpio: Too many arguments
ubuntu@ubuntu:/mnt/oldhome$ sudo find . -depth -print0 |sudo cpio --null --sparse --preserve-modification-time -pvd / mnt/newhome/
cpio: Too many arguments
ubuntu@ubuntu:/mnt/oldhome$ sudo find . -depth -print0 | sudo cpio --null --sparse --preserve-modification-time -pvd /mnt/newhome
0 blocks
ubuntu@ubuntu:/mnt/oldhome$

---

### Post by plucky on 2008-07-31
> sudo mount -t ext3/dev/hda3 /mnt/newhome


Should be ```
sudo mount -t ext3 /dev/hda3 /mnt/newhome
``` notice the extra space between ext3 and /dev/hda3


***What guide are you following?***

Also your "oldhome" partition isn't mounted correctly

Is your old home partition part of the "root" partition?


Good Luck

---

### Post by zvacet on 2008-07-31
@ **philetus**

Maybe [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") can help you.

---

### Post by philetus on 2008-07-31
> **plucky said:**
> Should be ```
sudo mount -t ext3 /dev/hda3 /mnt/newhome
``` notice the extra space between ext3 and /dev/hda3


***What guide are you following?***

Also your "oldhome" partition isn't mounted correctly

Is your old home partition part of the "root" partition?


Good Luck

What guide are you following?
[http://fullcirclemagazine.org/issue-15/](http://fullcirclemagazine.org/issue-15/)
How-To: Create a Separate Home Partition,

Is your old home partition part of the "root" partition?

Properties says: location /

---

### Post by zvacet on 2008-07-31
> Is your old home partition part of the "root" partition?

Properties says: location /

That means yes,it is on your root partition.

---

### Post by plucky on 2008-07-31
> **philetus said:**
> What guide are you following?
[http://fullcirclemagazine.org/issue-15/](http://fullcirclemagazine.org/issue-15/)
How-To: Create a Separate Home Partition,

Is your old home partition part of the "root" partition?

Properties says: location /

I have had a look at that guide,I don't think they mean for you to use the commands as published,as they are generic,but adapt them for your install.i.e mount /oldhome means mount your /home partition,not mount a partition called "oldhome".

I have used the guide **zvacet** has linked to,so give that a try,but adapt it for your install.

Good Luck

---

