---
title: "GRUB problem: I just get a GRUB prompt"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by klett on 2006-02-10
Hi,

I've had kubuntu along with windows xp running on my laptop for a few weeks.  My dual boot was configured like this: I had the windows loader in the MBR and grub in the / partition. Yesterday I noticed that Konqueror wasn't working fine (sometimes it froze) but I ignored it and shut down normally. This morning I started my computer, went through the windows loader menu and...after that I just got a grub prompt. I wasn't able to type anything and pressing esc didn't work.

I assumed that somehow it had corrupted and decided to reinstall kubuntu. I am still getting the grub prompt after a fresh install.

I have installed the 32bit version, but I have an amd64 processor. I've using a 64bit Ubuntu live cd to troubleshoot the problem. (I hope that this 32 and 64bit mixing doesn't matter).

This is what i've tried so far:

```
ubuntu@ubuntu:~$ sudo -s

root@ubuntu:~$ fdisk -l
Disk /dev/hda: 80.0GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units= cylinders of 16065*512=8225280 bytes

Device		Boot	Start	End	Blocks		Id	System
/dev/hda1	*	xxx	xxx	40981783+	7	HPFS/NTFS
/dev/hda2		xxx	xxx	6964177+	83	Linux
/dev/hda3		xxx	xxx	28917000	f	W95 Ext'd (LBA)
/dev/hda4		xxx	xxx	1285200		b	W95 FAT32
/dev/hda5		xxx	xxx	1044193+	xxx	Linux Swap/Solaris
/dev/hda6		xxx	xxx	8297509+	xxx	Linux
/dev/hda7		xxx	xxx	19575171	xxx	Linux

```
xxx is data I didn't copied. If it is necessary, I can provide it.
My laptop is HP and almost all of them come with a hidden partition. I guess that in this case it's /dev/hda3
```

root@ubuntu:~$ mkdir mysysimage

root@ubuntu:~$ mount /dev/hda2 mysysimage

root@ubuntu:~$ chroot mysysimage

root@ubuntu:/# ls /boot/grub
device.map menu.lst fat_stage1_5 reiserfs_stage1_5 e2fs_stage1_5 jfs_stage1_5
minix_stage1_5 xfs_stage1_5 stage1 stage2

root@ubuntu:/# cat /boot/grub/device.map
(hd0) /dev/hda

root@ubuntu:/# grub

grub> cat (hd0,1)/boot/grub/menu.lst
```

I will omit some obvious comments:
```

[I]default 0
timeout 10

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
###BEGIN AUTOMAGIC KERNEL LIST
## lines between AUTOMAGIC KERNEL LISTS
## markers will be modified by the debian
## update-grub script except for the default
## options below

## DO NOT UNCOMMENT THEM, just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## if you want special options for specific kernels
## use kopt_x_y_z where x.y.z is kernel version.
## Minor versions can be omitted
# kopt=root=/dev/hda2 ro

## default root device
# groot=(hd0,1)

##should update-grub create alternative automagic boot options
# alternative=true

##should update-grub lock alternative automagic boot options
# lockalternative=false

## altoption boot target option
## multiple altoptions are allowed
# altoptions=(recovery mode) single

## nonaltoption boot target option
## This option controls options to pass to only the
## primary kernel menu item
# nonaltoptions=quiet splash

## controls how many kernels should be put ino the menu.lst
## Only counts the first occurence of a kernel, not the
## alternative kernel options
#howmany=all

##should update-grub create memtest86 boot option
#memtest86=true

## End Default Options ##

title	Ubuntu, kernel 2.6.12-9-386
root	(hd0,1)
kernel	/boot/vmlinuz-2.6.12-9-386 root=dev/hda2 ro quiet splash
initrd	/boot/initrd.img-2.6.12-9-386
savedefault
boot

title	Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root	(hd0,1)
kernel	/boot/vmlinuz-2.6.12-9-386 root=dev/hda2 ro single
initrd	/boot/initrd.img-2.6.12-9-386
savedefault
boot

title	Ubuntu, memtest86+
root	(hd0,1)
kernel	/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

#This is a divider, added to separate the menu items below from the Debian
#ones

title	Other operating systems
root

#This entry automatically added by the debian installer for a non-linux OS
#on /dev/hda1

title	Microsoft Windows XP Home Edition
root	(hd0,0)
savedefault
chainloader +1
boot[/I]
```

```
grub> geometry (hd0)

drive 0x80: C/H/S=16383/255/63,
The number of sectors=156301488, /dev/hda

Partition num: 0, Filesystem type unknown
Partition num: 1, Filesystem type ext2fs
Partition num: 3, Filesystem type fat
Partition num: 4, Filesystem type unknown
Partition num: 5, Filesystem type ext2fs
Partition num: 6, Filesystem type ext2fs

grub> root (hd0,1)
Filesystem type is ext2fs, partition type 0x83

grub> kernel /boot/vmlinuz-2.6.12-9-386 root=dev/hda2 ro
[Linux-bzImage, setup=0x1c00, size=0x124b1b]

grub> initrd /boot/initrd.img-2.6.12-9-386

Error 16: Inconsistent filesystem structure

grub> quit
```

```
root@ubuntu:/# exit
root@ubuntu:~$ umount mysysimage
root@ubuntu:~$ fsck /dev/hda2
fsck 1.38 (30-Jun-2005) e2fsck 1.38 (30-Jun-2005)
/: clean, 11050/870912 files, 239874/1741044 blocks
```


Apparently the filesystem is OK. Then, why do i get that "Inconsistent filesystem structure" message?

I'm wondering if this may have something to do with the way I have manipulated my partition table.
I insert my installation CD, and follow the installation process. When I reach the partitioning part,
I create my partitions and set /dev/hda2 as / and bootable.Then, I go through the installation process
to the end. After that, if I try to boot my machine I get a "Missing operating system" message. Then,
I insert the installation CD again and go through the installation process until I reach the partitioning bit.
The partitions are still there but their mounting point has changed: now they are named /dev/hdax.
I rename them appropriately and set the windows partition to be bootable. I select continue and get a warning message
saying that I have to format / in order to make a clean install. I get an error message saying that the installation
hasn't been completed and I'm presented the installation process menu. I select to quit and reboot. The windows loader works
fine and offers me two options: windows or linux. If I select windows everything goes fine. However, if I select Linux
I get the grub prompt and a blinking cursor. I cannot type anything, I press esc and nothing happens. At that point
I'm forced to shut down the computer.

Any suggestions??

Thanks in advance!

---

### Post by lha on 2006-02-10
So are you using NTLDR to load grub? If you do, have you copied the boot sector of hda2 to a file in Windows and set NTLDR to use that file to load grub? The old grub image you have may not work with your new install. (You have installed grub to hda2's boot sector during install, haven't you?)

---

### Post by klett on 2006-02-10
That was it!! I was using an old copy of the boot sector to load grub...

Many thanks Iha!!

---

