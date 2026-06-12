---
title: "suddenly: EXT4?!?"
date: 2008-10-16
forum: General Help
---

### Post by bgugi on 2008-10-16
i now officially vow to never put this computer in standby again.

every once in a while, it won't come back. the problem is, it is sometimes accessing the hdd, and sometimes it damages the filesystem. i've killed the superblock before, but that was easily fixed with fsck. but this time is truly anomalous.

i tried to boot (i use grub), and got an error 15. boot from live cd, i can't mount /dev/sda6 (my linux partition), ubuntu thinks it is ext4 (i booted livecd). so i backed up with dd_rescue, then tried various tools. fsck and e2fsck didn't work, so i'm coming to you.

help?

---

### Post by caljohnsmith on 2008-10-16
Do you have an AMD 64 processor? If so, the solution to your problem may be simple:

[http://ubuntuforums.org/showthread.php?t=927831](http://ubuntuforums.org/showthread.php?t=927831)

Let me know if that applies to you.

---

### Post by bgugi on 2008-10-16
sorry, but that doesn't apply to me. my computer is back from the boring days of processors: 32-bit single core, 1.6ghz.

dell latitude d610 laptop.

the big problem is: what could make ubuntu think the partition is ext4? and what (if anything) can be done to fix it?

---

### Post by MaxIBoy on 2008-10-17
Ext3 filesystems can be mounted as Ext4 (limited backwards and forwards compatibility.) I am unsure as to whether or not the Ext4-only features will be activated when something like that happens.

---

### Post by caljohnsmith on 2008-10-17
How about first posting:
```
sudo fdisk -lu
```
Also, see if you can do a file system repair on your sda6 linux partition:
```
sudo fsck -y /dev/sda6
```
Please post the results of that command too.

---

### Post by bgugi on 2008-10-17
> **caljohnsmith said:**
> How about first posting:
```
sudo fdisk -lu
```
Also, see if you can do a file system repair on your sda6 linux partition:
```
sudo fsck -y /dev/sda6
```
Please post the results of that command too.

the dd_rescue copy is all i have; i had to reinstall ubuntu to get grub to be bootable again. is there a way i can run these on the file? (the system seems to treat it the same as /dev/sdax input, but i'm not sure about the first one)

---

### Post by caljohnsmith on 2008-10-17
> **bgugi said:**
> the dd_rescue copy is all i have; i had to reinstall ubuntu to get grub to be bootable again. is there a way i can run these on the file? (the system seems to treat it the same as /dev/sdax input, but i'm not sure about the first one)
When you used dd_rescue, did you copy the Ubuntu partition only or the entire HDD? If you copied the entire HDD, navigate to the folder where your HDD image is and do:
```
sudo fdisk -lu HDD.image
```
Replace HDD.image with the dd_rescue HDD image, and please post the results.

---

### Post by bgugi on 2008-10-18
> **caljohnsmith said:**
> When you used dd_rescue, did you copy the Ubuntu partition only or the entire HDD? 

just the ubuntu partiton

---

### Post by caljohnsmith on 2008-10-18
OK, if for example the dd_rescue Ubuntu partition image is "ubuntu.img", then navigate to the folder where it is and do:
```
sudo fsck -y ubuntu.img
```
I believe that should work, and after that try:
```
sudo losetup /dev/loop0 ubuntu.img
sudo mount /dev/loop0 /mnt
ls -l /mnt
```
And post the output of all the above commands.

---

### Post by bgugi on 2008-10-18
file is /media/disk/backup.img

> bgugi@OPERATOR:~$ sudo fsck -y /media/disk/backup.img
[sudo] password for bgugi: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Filesystem revision too high while trying to open /media/disk/backup.img
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


> bgugi@OPERATOR:~$ sudo losetup /dev/loop0 /media/disk/backup.img
bgugi@OPERATOR:~$ sudo mount /dev/loop0 /mnt
mount: unknown filesystem type 'ext4'
bgugi@OPERATOR:~$ ls -l /mnt
total 0
bgugi@OPERATOR:~$ 


---

### Post by caljohnsmith on 2008-10-18
Try mounting it as ext3 and see if it will let you:
```
sudo losetup /dev/loop0 /media/disk/backup.img
sudo mount -t ext3 /dev/loop0 /mnt
ls -l /mnt
```

---

### Post by bgugi on 2008-10-18
> bgugi@OPERATOR:~$ sudo losetup /dev/loop0 /media/disk/backup.img
[sudo] password for bgugi: 
bgugi@OPERATOR:~$ sudo mount -t ext3 /dev/loop0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


> bgugi@OPERATOR:~$ dmesg | tail
[   60.414186] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   60.414194] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   61.579644] loop: module loaded
[  128.124455] input: b43-phy0 as /devices/virtual/input/input18
[   64.053068] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   64.053075] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  128.333735] EXT3-fs: loop0: couldn't mount because of unsupported optional features (80008000).
[  128.612999] input: b43-phy0 as /devices/virtual/input/input19
[   64.288737] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   64.288744] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
bgugi@OPERATOR:~$ 


hmf...

---

### Post by bgugi on 2008-10-20
bump for help please?

---

### Post by bgugi on 2008-10-21
are there any live-cd distros that will mount/repair/etc ext4 to see if that is somehow what the filesystem has really become?

---

