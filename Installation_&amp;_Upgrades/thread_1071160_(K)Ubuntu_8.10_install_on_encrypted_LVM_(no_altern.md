---
title: "(K)Ubuntu 8.10 install on encrypted LVM (no alternate CD)"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by GauthierJM on 2009-02-15
Hi all. I am looking to install (K)Ubuntu 8.10 on an encrypted LVM. I cannot get this to work and I am sure I am screwing something up. Any help 

on what went wrong would be greatly appreciated.

I edited /etc/apt/sources.list and uncommented the universe section, and installed required software.

```

$ sudo apt-get update
$ sudo apt-get install cryptsetup initramfs-tools hashalot lvm2
$ sudo modprobe aes-i586
$ sudo modprobe dm-crypt
$ sudo modprobe dm-mod

```

Partitioned the drive like so:
```

$ sudo fdisk /dev/sda


The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)


Command (m for help): n
Command action
e extended
p primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-9729, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-9729, default 9729): +512M


Command (m for help): n
Command action
e extended
p primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (34-9729, default 34):
Using default value 34
Last cylinder or +size or +sizeM or +sizeK (34-9729, default 9729):
Using default value 9729


Command (m for help):t
Partition number (1-4): 2
Hex code (type L to list codes): 8e


Command (m for help):w

```

I checked the disk and filled with random data and encrypted.
```

$ sudo /sbin/badblocks -c 10240 -s -w -t random -v /dev/sda2
$ sudo dd if=/dev/urandom of=/dev/sda2
$ sudo cryptsetup -y --cipher aes-xts-plain --key-size 512 luksFormat /dev/sda2
WARNING!
========
This will overwrite data on /dev/sda2 irrevocably.


Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: (enter passphrase)
Verify passphrase: (repeat passphrase)


$ sudo cryptsetup luksOpen /dev/sda2 pvcrypt

```

Created the LVM
```

$ sudo pvcreate /dev/mapper/pvcrypt
$ sudo vgcreate VolGroup00 /dev/mapper/pvcrypt
$ sudo lvcreate -n swap -L 4G VolGroup00
$ sudo lvcreate -n home -L 10G VolGroup00
$ sudo lvcreate -n root -L 60G VolGroup00
$ sudo mke2fs -j /dev/sda1
$ sudo mkswap -L swap /dev/VolGroup00/swap
$ sudo mkfs -j /dev/VolGroup00/home -L home
$ sudo mkfs -j /dev/VolGroup00/root -L root

```

I proceeded with the installation as normal with exception of the partitioning. I mapped the drives listed above and the install goes smooth as 

silk. I then chroot into the install to install the required apps.
```

$ cd /mnt
$ sudo mkdir root
$ sudo mount -t ext3 /dev/mapper/VolGroup00-root /mnt/root
$ sudo mount -t ext3 /dev/sda1 /mnt/root/boot
$ sudo mount -t ext3 /dev/mapper/VolGroup00-home /mnt/root/home
$ sudo chroot /mnt/root
$(chroot) sudo mount -t proc proc /proc
$(chroot) sudo mount -t sysfs sys /sys
$(chroot) sudo mount -t devpts devpts /dev/pts
$(chroot) sudo apt-get update
$(chroot) sudo apt-get install cryptsetup hashalot initramfs-tools lvm2

```

Then I added this to my /etc/crypttab
```
pvcrypt         /dev/sda2       none            luks,retry=1,lvm=vg
```

I edited etc/initramfs-tools/modules to include:
aes-i586
dm-crypt
dm-mod
sha256

and rebuilt the ramfsdisk with
```
sudo update-initramfs -k all -c
```

I also added the following to /etc/initramfs-tools/conf.d/cryptroot 

```
CRYPTROOT=target=pvcrypt,source=/dev/sda2
```

When I reboot it prompts me to enter a passcode to unlock the device /dev/sda2. I know that I am typing the right password in and it say 

cryptsetup:cryptsetup failed, bad password or options? the it drops to initramfs.

Where did I go wrong?

Thanks

---

### Post by GauthierJM on 2009-02-16
Anyone? I would really like to figure this out without having to run to the alt install CD. I know it's been done. 

Thanks

---

### Post by Charlie708 on 2009-02-25
If you haven't solved the problem already, try using this guide as a base:
[http://polishlinux.org/linux/ubuntu/install-ubuntu-804-on-lvm2/](http://polishlinux.org/linux/ubuntu/install-ubuntu-804-on-lvm2/)

---

