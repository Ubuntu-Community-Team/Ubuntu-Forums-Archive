---
title: "Moving an existing installation from one physical disk to another"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by stromdal on 2009-01-16
I have a HTPC with MythBuntu that I've used for some time now, but now I suspect the system disk to fail within short; it is making a lot of noise. Being an old 20GB disk that I got for free, this is no tragedy; I already have a 40GB disk to replace the old one, but the work involved in setting the system up again is not too appealing - especially since I am a Linux novice.

What would be the best approach here? 
* Raw-copying the entire 20GB disk onto the 40GB disk or 
* making backup of the system settings from the 20GB disk, installing MythBuntu on the 40GB disk and using the backup to create an identical system again?

---

### Post by logos34 on 2009-01-16
clone the entire disk to new one with the dd command--that's the easiest IMO.

> Cloning an entire hard disk:
Code:

dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror

/dev/sda is the source. /dev/sdb is the target. Do not reverse the intended source and target. It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
Or copy it with **cp -a**.  Or use gparted 'move' function:

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

(the latter require you to reinstall grub to mbr of new disk.)

---

### Post by stromdal on 2009-01-17
I took your advice and did a 

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

The command seems to have worked fine, but after removing the old drive and booting I get a GRUB Error 2. I guess this is doe to GRUB not finding the correct partition to boot from, but I cant seem to solve the problem. 

When booting onto the system using a Live CD I run the commands

```
ubuntu@ubuntu:~$ sudo grub
grub> find /boot/grub/stage1

Error 15: File not found.
```

also: 

```
ubuntu@ubuntu:~$ sudo cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

```

At least the disks (there's one PATA 40GB which now contains the system and an unformatted SATA 1TB disk for media storage):

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32503250

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2373    19061091   83  Linux
/dev/sda2            2374        2482      875542+   5  Extended
/dev/sda5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

Any suggestions on how I should proceed to make the setup work?

---

### Post by logos34 on 2009-01-17
> **stromdal said:**
> 
```
ubuntu@ubuntu:~$ sudo cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

```


For cat, the partition has be mounted and you need to get the path correct (sth like '/media/disk/boot/grub/menu.lst').

But 'find' command should output 'root (hd0,0)' -->your / partition.

You've attempted to boot without 1TB disk connected?

Do an error check:

sudo fsck /dev/sda1

Try 

sudo grub

root (hd0,0)

setup (hd0)

quit

---

### Post by stromdal on 2009-01-18
No good:

```
ubuntu@ubuntu:/$ find menu.lst
find: menu.lst: No such file or directory
```

```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 
```

---

### Post by logos34 on 2009-01-18
> **stromdal said:**
> No good:

```
ubuntu@ubuntu:/$ find menu.lst
find: menu.lst: No such file or directory
```

```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 
```

The 'find' command needs to be run within the grub shell, and you have to provide the absolute path. 

Maybe the 40 GB drive is being seen as (hd1), in which case root (hd1,0).  But temporarily disconnecting the 1 TB would be better, in order to isolate the problem.
 
Did you run fsck?

then try the above again

Mount sda1 in nautilus file browser.  What does

ls -l /media/disk/boot/grub/

show?

---

### Post by stromdal on 2009-01-20
> **logos34 said:**
> ... temporarily disconnecting the 1 TB would be better, in order to isolate the problem.

Tried it. Made no difference. I'll try your other suggestions as soon as possible.

---

### Post by stromdal on 2009-01-22
> **logos34 said:**
> The 'find' command needs to be run within the grub shell, and you have to provide the absolute path.

Which means that I have to mount it, right?

> **logos34 said:**
> 
Did you run fsck?


This too can only be done if the drive is mounted, right?

> **logos34 said:**
> 
Mount sda1 in nautilus file browser.


Trying to mount the drive generates the following error:

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program or other error.

```
dmesg | tail
[ 3045.793069] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 146 not in group (block 0)!
[ 3045.797526] EXT3-fs: group descriptors corrupted!

```

Any suggestions?

---

### Post by stromdal on 2009-01-22
I think I found the problem. I connected the original 20GB HDD and removed the 40GB disk. When booting, GRUB is working fine, but the following error occurs:

```
Checking file systems...
fsck 1.40.8 (13-mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2 file system. If the device is valid and really contains an ext2 file system (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an altenate superblock: 
e2fsck -b 8193 <device> 

fsck died with exit status 8
                                                                      [failed]
* File system check failed

```

I'm only a n00b, but I'm guessing this is a Bad Thing (c) and might be the root cause why the mirrored disk is not functioning.

So I guess my only option is to make a clean install of the new disk and try to get as much of the old configurations transfered from the old disk to the new one. Despite the fsck error I _AM_ able to boot into Linux.

Any pointers on how I do a system backup of the old disk and transfer the settings to a fresh install on the new disk?

---

### Post by logos34 on 2009-01-22
> **stromdal said:**
> Which means that I have to mount it, right?


This too can only be done if the drive is mounted, right?

The partition does not need to be mounted to run grub shell 'find' command (counterintuitive though it may seem)...But it cannot be mounted when doing a filesystem check.


> **stromdal said:**
> 
So I guess my only option is to make a clean install of the new disk and try to get as much of the old configurations transfered from the old disk to the new one. Despite the fsck error I _AM_ able to boot into Linux.

Any pointers on how I do a system backup of the old disk and transfer the settings to a fresh install on the new disk?

+1  I'd go for a fresh install too at this point--no point wasting more time troubleshooting this.

I recommend first moving /home (which contains all your desktop settings and prefs) to a separate partition (see link in my signature).  Then backup all your installed apps (.debs) in /var/cache/apt/archive using [AptOnCD]("http://aptoncd.sourceforge.net/").  Either that or generate a list of installed pkgs for reinstallation like this:

dpkg --get-selections | grep -v deinstall > mypackages

To reinstall:

sudo apt-get update
sudo dpkg --set-selections < mypackages
sudo apt-get -u dselect-upgrade

or go into synaptic and install all selected packages.

good luck

ADD: On second thought, you might try simply copying your / over using the cp -a command, as I first suggested (after, of course, creating a ext3 partition on the 40 gb disk).  But you'll have to install grub to the MBR.  You might be able to avoid a reinstall.

---

### Post by nowhere@cox.net on 2009-02-27
From the way I read it, you had a 20GB PATA installed alone, cloned it to a 40GB PATA with dd, then installed a new 1TB SATA drive. Is this correct? If so then it is very likely that the order of the drives changed in your BIOS when you installed the SATA drive and Ubuntu/grub is not very good at automatically handling drive order when you have PATA and SATA drives installed simultaneously. 

Unfortunately, grub and the menu.lst file still give me fits with the PATA and SATA drives both installed so I had to trial and error the 0's and 1's until it worked. Also, booting into the bios setup and re-confirming the boot order seemed to make a difference too.

Maybe someone out there adept at manually configuring grub could help you through it.

---

