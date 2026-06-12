---
title: "Grub on RAID0, overwrite MBR"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by dontiego on 2009-01-11
Hi all!

I have wanted to use linux again for a great while, so I bought a new hard drive and installed ubuntu. I messed it all up, and could just recover my windows thanks to Super grub disk.
Although I'm not giving up, I need your help to minimize my risk of losing it all.

---
1. My setup
Disk1: a RAID0 array of 2 disks, with Windows XP.
Disk2: my new disk. An empty SATA disk. (well there is ubuntu on it since my last attempt, but I don't care)

---
2. What I've done
I put the ubuntu CD in my computer and installed.
Upon restart I got the grub Error 21 (disk not recognised?). At other times I got error 17.
I booted with Supergrubdisk, read on.
I restored the MBR with Supergrubdisk.

---
3. What I think I've learned, which I'd like someone to confirm
- Grub does not support RAID0 array. This means I cannot install grub on my disk1. True? Or is this only valid for SW RAID0? I think I have HW RAID0.
- Installing grub on Disk1 would overwrite the MBR, preventing me from starting Windows. Right? Or can it coexist on Disk1 together with my windows?
- When installing ubuntu, Grub gets installed on the first disk in the boot order. True?

---
4. What I think I should do
- set the boot order so that the first drive is Disk2.
- boot up on Ubuntu live CD and install. Grub gets installed on Disk2 and does not overwrite the MBR on Disk1.
- configure grub (first find out how) and modify /boot/grub/menu.lst (first find out what to write).

I do not suppose that this is right, but this is as right I can think.

---
5. What I wonder
- will grub on Disk2 be able to boot my RAID0 Disk1? In my different attempts to make it work, I remember seeing the grub menu showing only linux boots, not my XP disk1. [http://ubuntuforums.org/showthread.php?t=166237](http://ubuntuforums.org/showthread.php?t=166237)
- do I need to put /boot in its own partition?


I'd really appreciate any suggestion before I start installing ubuntu again.

Thanks for your time!

---

### Post by dontiego on 2009-01-11
Ok, I ran the popular boot info script, and got the following result.
I know I don't have input for my Windows partition in the menu.lst, but this should not prevent the start of ubuntu?

Still, I get error 17.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37073706

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000201


sfdisk -V /dev/sdb:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7327f626

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    39070079    19535008+  83  Linux
/dev/sdc2        39070080   238484924    99707422+   5  Extended
/dev/sdc5        39070143   234581129    97755493+  83  Linux
/dev/sdc6       234581193   238484924     1951866   82  Linux swap / Solaris

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="9e52c1e4-44e2-45de-b7bc-f718af236745" TYPE="ext3" 
/dev/sdc5: UUID="348242d3-b37c-41da-9541-a846a2549545" TYPE="ext3" 
/dev/sdc6: TYPE="swap" UUID="b14a787a-68cd-4f69-b2c5-332414e48539" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-rt/volatile type tmpfs (rw)
/dev/sdc5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)

=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9e52c1e4-44e2-45de-b7bc-f718af236745 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=9e52c1e4-44e2-45de-b7bc-f718af236745 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=9e52c1e4-44e2-45de-b7bc-f718af236745 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=9e52c1e4-44e2-45de-b7bc-f718af236745 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=348242d3-b37c-41da-9541-a846a2549545 /home           ext3    relatime        0       2
# /dev/sdc6
UUID=b14a787a-68cd-4f69-b2c5-332414e48539 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 17320
drwxr-xr-x  3 root root    4096 2009-01-11 15:56 .
drwxr-xr-x 21 root root    4096 2009-01-11 15:44 ..
-rw-r--r--  1 root root   85837 2008-06-18 20:23 config-2.6.24-19-rt
drwxr-xr-x  2 root root    4096 2009-01-11 15:56 grub
-rw-r--r--  1 root root 7563385 2009-01-11 15:56 initrd.img-2.6.24-19-rt
-rw-r--r--  1 root root 7032683 2009-01-11 15:38 initrd.img-2.6.24-19-rt.bak
-rw-r--r--  1 root root  103204 2007-09-28 12:06 memtest86+.bin
-rw-r--r--  1 root root  928278 2008-06-18 20:23 System.map-2.6.24-19-rt
-rw-r--r--  1 root root 1959832 2008-06-18 20:23 vmlinuz-2.6.24-19-rt

=============================== sdc1/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2009-01-11 15:56 .
drwxr-xr-x 3 root root   4096 2009-01-11 15:56 ..
-rw-r--r-- 1 root root    197 2009-01-11 15:56 default
-rw-r--r-- 1 root root     45 2009-01-11 15:56 device.map
-rw-r--r-- 1 root root   8056 2009-01-11 15:56 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-11 15:56 fat_stage1_5
-rw-r--r-- 1 root root     18 2009-01-11 15:56 installed-version
-rw-r--r-- 1 root root   8608 2009-01-11 15:56 jfs_stage1_5
-rw-r--r-- 1 root root   4241 2009-01-11 15:56 menu.lst
-rw-r--r-- 1 root root   7324 2009-01-11 15:56 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-11 15:56 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-11 15:56 stage1
-rw-r--r-- 1 root root 108356 2009-01-11 15:56 stage2
-rw-r--r-- 1 root root   9276 2009-01-11 15:56 xfs_stage1_5

=============================== StdErr Messages: ===============================

Disk /dev/sdb doesn't contain a valid partition table
```

It feels like the numbering of my sdc is strange. sdc1, sdc2, sdc5, sdc6, but not 3 or 4?

My device.map looks like this:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

sda and sdb are actually my RAID0 array with WinXP on.

Any thoughts? Is this problem related to the RAID0?
Thanks in advance!


Edit: now I tried
sudo grub
root (hd2,0)
setup (hd0)

to no av. I received no error while doing that, though.

---

### Post by caljohnsmith on 2009-01-11
> **dontiego said:**
> 
3. What I think I've learned, which I'd like someone to confirm
- Grub does not support RAID0 array. This means I cannot install grub on my disk1. True? Or is this only valid for SW RAID0? I think I have HW RAID0.
- Installing grub on Disk1 would overwrite the MBR, preventing me from starting Windows. Right? Or can it coexist on Disk1 together with my windows?
- When installing ubuntu, Grub gets installed on the first disk in the boot order. True?

I would say yes to everything above, because even though you could install Grub to the MBR of your RAID array and maybe get it working, it's not worth the frustration I think of trying. I like your next solution better:
> **dontiego said:**
> 
4. What I think I should do
- set the boot order so that the first drive is Disk2.
- boot up on Ubuntu live CD and install. Grub gets installed on Disk2 and does not overwrite the MBR on Disk1.
- configure grub (first find out how) and modify /boot/grub/menu.lst (first find out what to write).

I do not suppose that this is right, but this is as right I can think.

---
5. What I wonder
- will grub on Disk2 be able to boot my RAID0 Disk1? In my different attempts to make it work, I remember seeing the grub menu showing only linux boots, not my XP disk1. [http://ubuntuforums.org/showthread.php?t=166237](http://ubuntuforums.org/showthread.php?t=166237)
- do I need to put /boot in its own partition?


I'd really appreciate any suggestion before I start installing ubuntu again.

Thanks for your time!
The above scenario you describe of installing Grub to your HDD #2, and then setting your BIOS to boot that drive, definitely has my vote. You don't have to reinstall either it looks like, how about trying the following:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
That will install Grub to the MBR of your Ubuntu sdc drive so that you should be able to boot it OK. Next you'll need to modify its menu.lst slightly:
```
sudo mount /dev/sdc1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all the Ubuntu entries to use (hd0,0) similar to:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=9e52c1e4-44e2-45de-b7bc-f718af236745 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet
```
Also change the "# groot=(hd2,0)" line to:
```
# groot=(hd0,0)
```
Also, at the end of the menu.lst add:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Then reboot, set your BIOS to boot the Ubuntu drive, and you should be able to boot into Ubuntu if all goes well. Also try the two Windows entries from your Grub menu, and let me know exactly what happens when youy try them. We can work from there if you want.

---

### Post by dontiego on 2009-01-12
Great!
This is working fine.

Windows (hd1) works, Windows (hd2) does not.
Not so strange, I guess there is boot information only on one of the RAID disks.

I am very happy to get this thing working, but even happier to kind of understand what is going on! Thanks a lot!

For my education, what was that change of 
# groot=(hd0,0)
that you made me do?
Right code is not only right code, it is also right comments, is that it?

Now I'll go and tweak my grub a bit more, colors, default choices, and so on.

You made my day!

---

### Post by caljohnsmith on 2009-01-12
Glad to hear that worked OK. About the "groot" line in your menu.lst, that's the line that the Grub automatic updater uses to know which drive/partition your main Ubuntu install is on; even though it is commented so that it isn't used on start up, the "update-grub" command that is run when you get a new kernel looks at that line to know which "root (hdX,Y)" it should use for the new Ubuntu entry. Anyway, cheers and have fun with your Ubuntu install. :)

---

