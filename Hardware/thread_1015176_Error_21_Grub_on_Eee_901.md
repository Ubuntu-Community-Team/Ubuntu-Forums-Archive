---
title: "Error 21 Grub on Eee 901"
date: 2008-12-18
forum: Hardware
---

### Post by skykaptain on 2008-12-18
I have a Eee PC 901 with the default Xandros on the HHD and Ubuntu Eee on a SD card. When I remove the SD card I get a Grub Error 21 on boot up. I would like to be able to boot into Xandros without the SD card in so I maybe able to have more OS's on different SD cards. 

I know Ubuntu Eee is not part of Ubuntu but I figured that since it is based off Ubuntu, the Grub menu will close to each other. I have tried to get help from the Ubuntu Eee forums but no one has really helped.

---

### Post by InlawBiker on 2008-12-18
Error 21 means an expected device isn't present.  I suspect you have written your master boot record (MBR) to the SD card.  When Grub goes looking for the MBR it's missing and you get the error.  Sound accurate?

You should be able to go back and re-write the boot partition info into the Xandros internal HDD instead of to the SD card.

Do some googling on eee, menu.lst, dual-boot, ubuntu, grub.

---

### Post by caljohnsmith on 2008-12-18
It sounds like what happened is you accepted the default settings for Grub when you installed Ubuntu to the SD card; by default Grub gets installed to /dev/sda which would be your internal Xandros HDD. To correct the problem, you can first install Grub to the MBR of your SD card by doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0). If it returns any results where X is 0, don't use that one, use the one where X is 1. Use that result as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Also, which boot loader does Xandros use? Does it also use Grub?

---

### Post by skykaptain on 2008-12-18
Ok, good news and bad news. The good news is I can boot without the SD card. The bad news is I cannot boot from the SD card and when I try I get Error 15: File not found for both Ubuntu and Xandros. I would have posted the results but I did read that far down, I got excited.

---

### Post by caljohnsmith on 2008-12-18
> **skykaptain said:**
> Ok, good news and bad news. The good news is I can boot without the SD card. The bad news is I cannot boot from the SD card and when I try I get Error 15: File not found for both Ubuntu and Xandros. I would have posted the results but I did read that far down, I got excited.
OK, that's great news; so how about booting the SD card again, press ESC on to get the Grub menu (if there is a message saying to do that), select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by skykaptain on 2008-12-18
Ok, it worked for a while. I got it to boot by changing "root(hd2,0)" to "root(hd0,0)" but when I updated Grub, after changing it doing the above changes to menu.lst, I was given a list of updates. I picked the top one, something about adding the changes or updating, I don't really remember. After that I restarted and now I am still getting Error 15's. The Grub menu, on boot up, now has more options to choose from and none work.

They are:
```
root(hd0,0)
kernel /boot/vwlinuz-2.6.24-21-eeepc root=UUID=06dec0d-4d7d-4fe7-bc->
initrd /boot/initrd.img-2.6.24-21-eeepc
quiet
root(hd0,0)
kernel /boot/vmlinuz-2.21.4-eeepc quiet rw vga=785 irqpoll root=/d->
initrd /boot/initramfs-eeepc.img
savedefault
boot
```

I hope that helps because I have no idea what it any of it means.

---

### Post by caljohnsmith on 2008-12-18
OK, from your Live CD, how about posting the output of:
```
sudo fdisk -lu
```
And then for whichever is your SD card Ubuntu partition (maybe sdb1), do:
```
sudo mount /dev/[COLOR="Blue"]sdb1[/COLOR] /mnt
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
sudo blkid
```
So change sdb1 above if that is not the correct partition. Please post the results.

---

### Post by skykaptain on 2008-12-18
Ok, here is the results from "fdisk." Sda is the original OS, sdb is the storage, sdc is the SD  card, sdd is the flash drive I use as a Live CD.

```
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb38fb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     6425999     3212968+  83  Linux
/dev/sda2         6426000     7839719      706860   83  Linux
/dev/sda3         7839720     7855784        8032+   c  W95 FAT32 (LBA)
/dev/sda4         7855785     7871849        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31519529    15759733+  83  Linux

Disk /dev/sdc: 4075 MB, 4075290624 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001aee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     7502354     3751146   83  Linux
/dev/sdc2         7502355     7952174      224910    5  Extended
/dev/sdc5         7502418     7952174      224878+  82  Linux swap / Solaris

Disk /dev/sdd: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          80    15663103     7831512    c  W95 FAT32 (LBA)

```

Here is the results from the other command. I don't know if I entered the first one correctly.

```
ubuntu@ubuntu:~$ sudo mount /dev/sbc /mnt ls -l /mnt/boot cat /mnt/boot/grub/menu.lst
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
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="15fb1bc0-1a9d-448f-8f49-e01dcc163a24" TYPE="ext2" 
/dev/sda2: LABEL="USER" UUID="c1402c2d-53fb-491d-9b8e-15eb1c253a4f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: SEC_TYPE="msdos" LABEL="BIOS" UUID="4861-2962" TYPE="vfat" 
/dev/sdb1: LABEL="HOME" UUID="aac780c4-5c91-4b85-bcb6-e2d99d76c605" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="08dece0d-4d7d-4fe7-bc9f-d691a014c6c8" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="71350b6c-72e8-49f1-be27-237ce3e26b2d" 
/dev/sdd1: LABEL="VANCE-2" UUID="40C3-25B3" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
```

---

### Post by caljohnsmith on 2008-12-18
OK, how about posting:
```
sudo mount /dev/sdc1 /mnt
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```

---

### Post by skykaptain on 2008-12-18
This good?

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 12868
-rw-r--r-- 1 root root   67648 2008-08-22 20:03 config-2.6.24-21-eeepc
drwxr-xr-x 2 root root    4096 2008-12-18 18:02 grub
-rw-r--r-- 1 root root 5109751 2008-12-08 20:54 initrd.img-2.6.24-21-eeepc
-rw-r--r-- 1 root root 5109512 2008-12-01 15:05 initrd.img-2.6.24-21-eeepc.bak
-rw-r--r-- 1 root root  103204 2008-08-22 20:03 memtest86+.bin
-rw-r--r-- 1 root root  879903 2008-08-22 20:03 System.map-2.6.24-21-eeepc
-rw-r--r-- 1 root root 1850200 2008-08-22 20:03 vmlinuz-2.6.24-21-eeepc
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst

```

---

### Post by caljohnsmith on 2008-12-18
OK, while you still have sdc1 mounted on /mnt, please post the output of:
```
cat /mnt/grub/menu.lst
```
Also, how did you install Ubuntu to the SD card? It looks like sdc1 is just a "/boot" partition. Do you know which is the Ubuntu root "/" partition?

---

### Post by skykaptain on 2008-12-18
I don't think this right but here it is.

```
ubuntu@ubuntu:~$ cat /mnt/grub/menu.lst
cat: /mnt/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 

```

I don't remember what is the root directory was/is.

---

### Post by caljohnsmith on 2008-12-18
OK, how about trying the following:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo sh boot_info_script.txt
```
That will create a "boot_info_results.txt" file on your desktop; please copy/paste the contents of that file to your next post. If for some reason you get any errors with that script, please post:
```
ls -l /mnt/grub
```

---

### Post by skykaptain on 2008-12-18
Ok, here it is:
```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on boot drive #4 in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdc and looks on the same drive in partition #1 for its boot files.
Syslinux is installed in the MBR of /dev/sdd

sda1:
    File system:  ext2
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot/grub/grub.conf /boot /boot/grub

sda2:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present: 

sda3:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda4:
    File system:  Extended Partition

sdb1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdc1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sdc2:
    File system:  Extended Partition

sdc5:
    File system:  swap

sdd1:
    File system:  vfat
    Mounting failed:  
mount: /dev/sdd1 already mounted or sdd1 busy


Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb38fb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     6425999     3212968+  83  Linux
/dev/sda2         6426000     7839719      706860   83  Linux
/dev/sda3         7839720     7855784        8032+   c  W95 FAT32 (LBA)
/dev/sda4         7855785     7871849        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31519529    15759733+  83  Linux

Disk /dev/sdc: 4075 MB, 4075290624 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001aee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     7502354     3751146   83  Linux
/dev/sdc2         7502355     7952174      224910    5  Extended
/dev/sdc5         7502418     7952174      224878+  82  Linux swap / Solaris

Disk /dev/sdd: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          80    15663103     7831512    c  W95 FAT32 (LBA)
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  6425937, Id=83, bootable
/dev/sda2 : start=  6426000, size=  1413720, Id=83
/dev/sda3 : start=  7839720, size=    16065, Id= c
/dev/sda4 : start=  7855785, size=    16065, Id=ef
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 31519467, Id=83, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=  7502292, Id=83
/dev/sdc2 : start=  7502355, size=   449820, Id= 5
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start=  7502418, size=   449757, Id=82
# partition table of /dev/sdd
unit: sectors

/dev/sdd1 : start=       80, size= 15663024, Id= c, bootable
/dev/sdd2 : start=        0, size=        0, Id= 0
/dev/sdd3 : start=        0, size=        0, Id= 0
/dev/sdd4 : start=        0, size=        0, Id= 0

sda1/boot/grub/menu.lst

#
# Configured by Xandros Configuration system.
#
hiddenmenu
# default boot entry
default=0

# Boot automatically after 1 second.
timeout=0

# Fallback to Configure.
fallback=2

title Normal Boot
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1
	initrd /boot/initramfs-eeepc.img

title Perform Disk Scan
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y
	initrd /boot/initramfs-eeepc.img

title Restore Factory Settings
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y
	initrd /boot/initramfs-eeepc.img

sda1/boot/grub/grub.conf

#
# Configured by Xandros Configuration system.
#
hiddenmenu
# default boot entry
default=0

# Boot automatically after 1 second.
timeout=0

# Fallback to Configure.
fallback=2

title Normal Boot
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1
	initrd /boot/initramfs-eeepc.img

title Perform Disk Scan
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y
	initrd /boot/initramfs-eeepc.img

title Restore Factory Settings
	root (0x80,0)
	kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y
	initrd /boot/initramfs-eeepc.img

sda1/boot

total 4367
drwxr-xr-x  3 root root    1024 2008-06-17 13:41 .
drwxr-xr-x 25 root root    1024 2008-06-17 13:43 ..
-rw-r--r--  1 root root   44962 2008-02-13 20:19 config-2.6.21.4-eeepc
drwxr-xr-x  2 root root    1024 2008-06-03 15:16 grub
-rw-r--r--  1 root root 1092527 2008-04-21 19:13 initramfs-eeepc.img
-rw-r--r--  1 root root      49 2008-05-05 15:41 patches-2.6.21.4-eeepc
-rw-r--r--  1 root root  614400 2008-06-13 18:29 shutdown.fb
-rw-r--r--  1 root root  614400 2008-06-13 18:29 startup.fb
-rw-r--r--  1 root root  747514 2008-05-05 15:41 System.map-2.6.21.4-eeepc
-rw-r--r--  1 root root 1326712 2008-05-05 15:41 vmlinuz-2.6.21.4-eeepc

sda1/boot/grub

total 127
drwxr-xr-x 2 root root   1024 2008-06-03 15:16 .
drwxr-xr-x 3 root root   1024 2008-06-17 13:41 ..
-rw-r--r-- 1 root root     66 2007-05-23 15:59 device.map
-rw-r--r-- 1 root root   7520 2008-06-03 15:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7392 2008-06-03 15:16 fat_stage1_5
lrwxrwxrwx 1 root root      8 2008-06-03 15:16 grub.conf -> menu.lst
-rw-r--r-- 1 root root    676 2007-10-22 18:30 menu.lst
-rw-r--r-- 1 root root    512 2008-06-03 15:16 stage1
-rw-r--r-- 1 root root 107144 2008-06-03 15:16 stage2

sdc1/boot/grub/menu.lst

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=vga=785 irqpoll root=/dev/sda1

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu Eee 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro vga=785 irqpoll root=/dev/sda1
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro single
#initrd		/boot/initrd.img-2.6.24-21-eeepc

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Normal Boot
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Perform Disk Scan
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y 
#initrd		/boot/initramfs-eeepc.img
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Restore Factory Settings
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y 
#initrd		/boot/initramfs-eeepc.img
#savedefault
#boot


sdc1/boot

total 12876
drwxr-xr-x  3 root root    4096 2008-12-08 20:54 .
drwxr-xr-x 21 root root    4096 2008-12-10 20:43 ..
-rw-r--r--  1 root root   67648 2008-08-22 20:03 config-2.6.24-21-eeepc
drwxr-xr-x  2 root root    4096 2008-12-18 18:02 grub
-rw-r--r--  1 root root 5109751 2008-12-08 20:54 initrd.img-2.6.24-21-eeepc
-rw-r--r--  1 root root 5109512 2008-12-01 15:05 initrd.img-2.6.24-21-eeepc.bak
-rw-r--r--  1 root root  103204 2008-08-22 20:03 memtest86+.bin
-rw-r--r--  1 root root  879903 2008-08-22 20:03 System.map-2.6.24-21-eeepc
-rw-r--r--  1 root root 1850200 2008-08-22 20:03 vmlinuz-2.6.24-21-eeepc

sdc1/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2008-12-18 18:02 .
drwxr-xr-x 3 root root   4096 2008-12-08 20:54 ..
-rw-r--r-- 1 root root    197 2008-12-05 16:30 default
-rw-r--r-- 1 root root     60 2008-11-30 19:14 device.map
-rw-r--r-- 1 root root   8056 2008-12-05 16:30 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-05 16:30 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-05 16:30 installed-version
-rw-r--r-- 1 root root   8608 2008-12-05 16:30 jfs_stage1_5
-rw-r--r-- 1 root root   5214 2008-12-18 18:02 menu.lst
-rw-r--r-- 1 root root   5237 2008-12-18 22:49 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-05 16:30 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-05 16:30 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-05 16:30 stage1
-rw-r--r-- 1 root root 108356 2008-12-05 16:30 stage2
-rw-r--r-- 1 root root   9276 2008-12-05 16:30 xfs_stage1_5

StdErr Messages 

/dev/sda4: unknown volume type
/dev/sdc2: unknown volume type
cat: /tmp/BootInfo0/Unknown_MBR: No such file or directory
```

---

### Post by caljohnsmith on 2008-12-18
OK, so when you boot your SD card and get the Grub menu, what exactly happens when you choose the "Ubuntu Eee 8.04" entry? Which Grub error do you get?

---

### Post by skykaptain on 2008-12-18
> **caljohnsmith said:**
> OK, so when you boot your SD card and get the Grub menu, what exactly happens when you choose the "Ubuntu Eee 8.04" entry? Which Grub error do you get?

Error 15: File not found

---

### Post by caljohnsmith on 2008-12-18
How about doing:
```
sudo sfdisk -A1 /dev/sdc
sudo mkdir /tmp/sdc1
sudo mount /dev/sdc1 /tmp/sdc1
gksudo gedit /tmp/sdc1/boot/grub/menu.lst

```
And delete the "root /dev/sda1" at the end of the kernel line:
```
title		Ubuntu Eee 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro vga=785 irqpoll [COLOR="Blue"]root=/dev/sda1[/COLOR]  [COLOR="Red"]<--delete[/COLOR] 
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

```
Reboot, and let me know again what happens when you choose Ubuntu Eee 8.04 from the Grub menu.

---

### Post by skykaptain on 2008-12-18
Ok, I am able to boot without the Live USB but, from the SD card, only the recovery boot works. When I try the original Ubuntu it just stays at a blank black screen.

---

### Post by caljohnsmith on 2008-12-19
OK, at least we're making progress. How about rebooting and when you get the Grub menu on start up, select the "Ubuntu Eee 8.04 entry", press "e" to edit it, select the "kernel" line, press "e" to edit it, and then how about deleting the "vga=785 irqpoll" options at the end and replace them with "quiet splash". Press enter to save the change and "b" to boot. If that doesn't work, do you remember what kernel options you need to successfully boot Ubuntu? In other words, do you remember if you need either "vga=785" or "irqpoll" for example?

How about posting the following:
```
sudo mount /dev/sdc1 /mnt
cat /mnt/boot/grub/menu.lst~
```

---

### Post by skykaptain on 2008-12-19
Ok, deleting "vga=785 irqpoll" worked, I can get into Ubuntu without going through the recovery. Should I make that change in Grub?

```
sudo mount /dev/sdc1 /mnt
cat /mnt/boot/grub/menu.lst~
vance@HAL-2008:~$ sudo mount /dev/sdc1 /mnt
vance@HAL-2008:~$ cat /mnt/boot/grub/menu.lst~
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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=vga=785 irqpoll root=/dev/sda1

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu Eee 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro vga=785 irqpoll
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro single
initrd		/boot/initrd.img-2.6.24-21-eeepc

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Normal Boot
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Perform Disk Scan
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y 
#initrd		/boot/initramfs-eeepc.img
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Restore Factory Settings
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y 
#initrd		/boot/initramfs-eeepc.img
#savedefault
#boot

```

---

### Post by caljohnsmith on 2008-12-19
> **skykaptain said:**
> Ok, deleting "vga=785 irqpoll" worked, I can get into Ubuntu without going through the recovery. Should I make that change in Grub?

Yes, as long as everything seems to be working OK, you can make the changes to your menu.lst. Did you also add the "quiet splash" options, and did that work?

---

### Post by skykaptain on 2008-12-19
> **caljohnsmith said:**
> Yes, as long as everything seems to be working OK, you can make the changes to your menu.lst. Did you also add the "quiet splash" options, and did that work?

Yeah, I forgot to mention that but yes, that worked. With using the Grub menu, on boot, I get a Error 15 when I try to select the original OS. It's not much of a problem but it would be nice if I could do that. Thanks for your help.

---

### Post by caljohnsmith on 2008-12-19
I don't think I understand--if you want to modify your menu.lst with the changes, go ahead and boot into Ubuntu by modifying the Grub menu on start up to edit the kernel options, and once you are in Ubuntu, you can do:
```
gksudo gedit /boot/grub/menu.lst
```
And then edit the Ubuntu entries to make the changes permanent. Also, for whichever kernel options worked, which I assume was "quiet splash", then you'll also want to edit the "defoptions" line to use the same kernel options:
```
# defoptions=quiet splash
```
That way when you get new kernel upgrades, your menu.lst should hopefully not break again. So is that what you mean or did I misunderstand?

---

### Post by skykaptain on 2008-12-19
I understand and get what you mean and it works but what I meant is on my Grub menu, I have two choices to boot into, Ubuntu and Xandros. I can boot into Ubuntu fine but I can't boot into Xandros through Grub. Should I just comment it out or is there some way I can fix it?

---

### Post by caljohnsmith on 2008-12-19
I'm looking at the menu.lst from your Ubuntu sdc1 partition in your post #14, and I don't see any entries for Xandros; did I miss something? Can you post the contents of you menu.lst again and show me what you mean?

---

### Post by skykaptain on 2008-12-19
Sorry, it is titled as "Normal Boot," not Xandros.

```
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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=vga=785 irqpoll root=/dev/sda1

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu Eee 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

#title		Ubuntu 8.04 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=08dece0d-4d7d-4fe7-bc9f-d691a014c6c8 ro single
#initrd		/boot/initrd.img-2.6.24-21-eeepc

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Normal Boot
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Perform Disk Scan
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y 
#initrd		/boot/initramfs-eeepc.img
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
#title		Restore Factory Settings
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y 
#initrd		/boot/initramfs-eeepc.img
#savedefault
#boot

```

---

### Post by caljohnsmith on 2008-12-19
OK, while you are still in Ubuntu please post:
```
cat /boot/grub/device.map
```
Also, in order to boot Xandros from your SD card Grub menu, I think the best way to go about this is if you can tell me what boot drive the Xandros sda drive is. To do that, go ahead and reboot, and when you get the Grub menu on start up, press "c" to get the Grub command line. Then do:
```
grub> geometry (hd1)
grub> geometry (hd2)
grub> geometry (hd3)
```
Each of those commands will show the drive size in sectors and also the partitions. Please tell me which drive (hdX) has four partitions on it, because that should be your sda drive.

---

### Post by skykaptain on 2008-12-19
```
vance@HAL-2008:~$ cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

---

### Post by skykaptain on 2008-12-19
Hd2 has four partitions.

---

### Post by caljohnsmith on 2008-12-19
OK, first open your device.map with:
```
gksudo gedit /boot/grub/device.map
```
and change it to:
```

(hd0)	/dev/sdc
(hd2)	/dev/sda
```
Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Xandros entry to:
```
title		Normal Boot
root		[COLOR="Blue"](hd2,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 
initrd		/boot/initramfs-eeepc.img
savedefault
boot
```
Save, reboot, and let me know exactly what happens when you choose "Normal Boot" from the Grub menu.

---

### Post by skykaptain on 2008-12-19
> **caljohnsmith said:**
> 
Save, reboot, and let me know exactly what happens when you choose "Normal Boot" from the Grub menu.

Sweet, it worked. It booted into Xandros. Thanks again.

---

### Post by caljohnsmith on 2008-12-19
Glad to hear that did the trick; cheers and have fun with Ubuntu and Xandros. :)

---

