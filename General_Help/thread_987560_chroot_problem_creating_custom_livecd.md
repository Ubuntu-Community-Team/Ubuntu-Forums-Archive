---
title: "chroot problem creating custom livecd"
date: 2008-11-19
forum: General Help
---

### Post by zen_cat on 2008-11-19
Hi,
    I'm having my first go at trying to create custom livecd, following the instructions at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization). When I get to running chroot ("sudo chroot edit") I'm getting the following error:

```
chroot: cannot run command `/bin/bash': Exec format error
```

I've downloaded and run the automatic script mentioned on the wiki, but it fails at the same point.

I'm running i386 Hardy and trying to customize an AMD64 copy of Intrepid - would that be the issue?

---

### Post by caljohnsmith on 2008-11-19
How about posting your entire terminal session starting from where you begin to follow the tutorial, because that would help greatly in order to troubleshoot your problem.

---

### Post by zen_cat on 2008-11-19
Certainly - here's what I have:

```
rhart@rhart01:~$ sudo apt-get install squashfs-tools genisoimage qemu kvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
squashfs-tools is already the newest version.
genisoimage is already the newest version.
qemu is already the newest version.
kvm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rhart@rhart01:~$ sudo modprobe squashfs
rhart@rhart01:~$ mkdir ~/live
rhart@rhart01:~$ mv ubuntu-8.10-desktop-amd64.iso ~/live
rhart@rhart01:~$ cd ~/live
rhart@rhart01:~/live$ mkdir mnt
rhart@rhart01:~/live$ sudo mount -o loop ubuntu-8.10-desktop-amd64.iso mnt
rhart@rhart01:~/live$ mkdir extract-cd
rhart@rhart01:~/live$ rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
rhart@rhart01:~/live$ mkdir squashfs
rhart@rhart01:~/live$ sudo mount -t squashfs -o loop mnt/casper/filesystem.squashfs squashfs
rhart@rhart01:~/live$ mkdir edit
rhart@rhart01:~/live$ sudo cp -a squashfs/* edit/
rhart@rhart01:~/live$ sudo cp /etc/resolv.conf edit/etc/
rhart@rhart01:~/live$ sudo cp /etc/hosts edit/etc/
rhart@rhart01:~/live$ sudo mount --bind /dev/ edit/dev
rhart@rhart01:~/live$ sudo chroot edit
chroot: cannot run command `/bin/bash': Exec format error
rhart@rhart01:~/live$ 
```

---

### Post by caljohnsmith on 2008-11-19
OK, how about posting:
```
ls -l ~/live/mnt ~/live/mnt/bin/bash
```
I'm thinking though you're probably right about it being an issue with trying to work on a 64-bit Live CD when you are in 32-bit Ubuntu.

---

### Post by zen_cat on 2008-11-19
```
rhart@rhart01:~/live$ ls -l ~/live/mnt ~/live/mnt/bin/bash
ls: cannot access /home/rhart/live/mnt/bin/bash: No such file or directory
/home/rhart/live/mnt:
total 1344
-r--r--r-- 1 root root      40 2008-10-30 09:02 autorun.inf
dr-xr-xr-x 2 root root    2048 2008-10-30 09:05 casper
dr-xr-xr-x 3 root root    2048 2008-10-30 09:05 dists
dr-xr-xr-x 2 root root    2048 2008-10-30 09:05 install
dr-xr-xr-x 2 root root   12288 2008-10-30 09:05 isolinux
-r--r--r-- 1 root root    5010 2008-10-30 09:05 md5sum.txt
dr-xr-xr-x 2 root root    2048 2008-10-30 09:05 pics
dr-xr-xr-x 4 root root    2048 2008-10-30 09:05 pool
dr-xr-xr-x 2 root root    2048 2008-10-30 09:05 preseed
-r--r--r-- 1 root root     226 2008-10-30 09:05 README.diskdefines
lr-xr-xr-x 1 root root       1 2008-10-30 09:05 ubuntu -> .
-r--r--r-- 1 root root  199517 2008-09-19 00:14 umenu.exe
-r--r--r-- 1 root root 1145132 2008-10-28 04:40 wubi.exe
rhart@rhart01:~/live$ 

```

I'm going to burn a copy of the 64bit install onto a spare machine and give it another go. Thanks,

Rafe

---

