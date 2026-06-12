---
title: "Convert a single drive system to RAID"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by giannozzo on 2009-03-12
Hi all!
I'm trying to convert a running installation of a Ubuntu server 7.10 AMD64 running on a single drive to a RAID 1 system, but I'm stuck at the boot with a BusyBox shell.

The machine has two identical SATA drives, the system is at the moment installed on partition /dev/sda1 (/dev/sda2 being the swap partition).
These are the steps I did until now:
[LIST=1]
[*] made a backup of the system on an external drive
[*] cfdisk /dev/sdb to have exactly the same partitions of /dev/sda 
[*] created md0 device node (mknod /dev/md0 b 9 0) 
[*] installed mdadm 
[*] created raid device:
```
mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sdb1
``` 
[*] checked /proc/mdstat (it's ok) 
[*] created filesystem on /dev/md0 
[*] mounted /dev/md0 on /mnt/md0 and copied data from /dev/sda1 (/) to /dev/md0 (/mnt/md0/) via rsync excluding content of /sys, /proc, /dev, /mnt 
[*] edited grub menu in /mnt/md0:
modified menu.lst just in "root" argument with "root=/dev/md0" 
[*] edited /etc/fstab in /mnt/md0 specifying that root has to be mounted from /dev/md0 
[*] chrooted to /mnt/md0 
[*] updated ramdisk with update-initramfs 
[*] installed grub on the new raid disk:
```
root (hd1,0)
setup (hd1)
```
All went ok 
[*] rebooted and changed BIOS setting to start from the new disk 
[/LIST]

At that point, grub starts, but after about 1 minute I get **[COLOR="Red"]an error[/COLOR]** and then a BusyBox shell.
This is the error:
```
     Check root= bootarg cat /proc/cmdline
     or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/md0 does not exist. Dropping to a shell!

```

If I check with "cat /proc/cmdline" I get the following:

```
root=/dev/md0 ro quiet splash
```

which looks to be correct
List of modules shows that raid modules and md_mod are present.
Command **mdadm **is present
If I give the command:
```
mdadm --assemble /dev/md0 
```
I get the following:
```
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: /dev/md0 not identified in config file.

```

"ls -l /dev/md0" shows that device md0 is present (or at least, it seems):
```
brw-rw----   1  0     0     9,   0  /dev/md0
```

Any help or suggestion would be greatly appreciated.

Fortunately I still get a fully working system if I boot from the first hard drive.

---

