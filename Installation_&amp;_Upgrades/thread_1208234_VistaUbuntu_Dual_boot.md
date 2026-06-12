---
title: "Vista/Ubuntu Dual boot"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by NastyNative on 2009-07-09
Greetings

I'm currently running Vista 64bit on a Raid (stripped) 
2 hitachi drives.

This past weekend I purchased a 160 GB WD drive

I installed it in my machine and did a ubuntu installation

"/" 20GB Primary ( I also added the Bootloader on this partition)
"/home" 20GB Logical
"swap" 2gb
"Fat32" 38GB windows/ubuntu file sharing
"NTFS" 80 GB has not been partition yet I will do it from vista 
so I can have more storage

After the installation It booted right into Vista.

I know I can go into the Bios and change the drive boot order im afraid of damaging my raid.

How can I boot my ubuntu installation?

I installed 9.04 64bit

---

### Post by lindsay7 on 2009-07-09
Use the ubuntu live cd and type sudo fdisk -l (letter l not number 1) in the terminal and past the results here.

---

### Post by NastyNative on 2009-07-09
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -i
fdisk: invalid option -- 'i'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

### Post by lindsay7 on 2009-07-09
use the letter l not i, l as in left.

---

### Post by merlinus on 2009-07-09
l is a lowercase L, not an i.

---

### Post by NastyNative on 2009-07-09
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe80dce22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20023   160833536    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x540b8ddd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1216     9767488+  83  Linux
/dev/sdc2           10199       19457    74366976    6  FAT16
/dev/sdc3            1217       10198    72147915    5  Extended
/dev/sdc5            7768       10198    19527007+  83  Linux
/dev/sdc6            7524        7766     1951866   82  Linux swap / Solaris
/dev/sdc7            1217        7522    50652882    b  W95 FAT32

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by lindsay7 on 2009-07-09
type the following in the terminal and post the results,

cat /boot/grub/menu.lst   (again that is the letter l in lst).

---

### Post by NastyNative on 2009-07-09
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by lindsay7 on 2009-07-09
try running the command as follows

sudo cat /boot/grub/menu.lst


Also here is some info that may help you

[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by NastyNative on 2009-07-09
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo cat/boot/grub/menu/lst
sudo: cat/boot/grub/menu/lst: command not found
ubuntu@ubuntu:~$ sudo cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 

Hey lindsay I appreciate your help very much.

Remember I dont want to run ubuntu from my raid drive 
I have way too many important programs and files 
It would be a shame to mess it up.

I don't really understand why im not getting the dual boot option if I installed the boot loader on the primary ubuntu partition

````````````````````````````````
ubuntu@ubuntu:~$ sudo cat/boot/grub/menu.lst
sudo: cat/boot/grub/menu.lst: command not found
ubuntu@ubuntu:~$

---

### Post by lindsay7 on 2009-07-09
Try the command again. there is a space between cat and /boot

sudo cat /boot/grub/menu.lst   you can copy and paste this if you want.

---

### Post by NastyNative on 2009-07-09
ubuntu@ubuntu:~$ sudo cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 


Im still getting the samething?

What does it mean?

``````````````````
I went to the actual menu.lst file and this is what it says I dont know if this will help you 

``````````````````````
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
# kopt=root=UUID=82dbf9c4-4f3d-4ae2-9571-75675ad92bfb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82dbf9c4-4f3d-4ae2-9571-75675ad92bfb

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		82dbf9c4-4f3d-4ae2-9571-75675ad92bfb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=82dbf9c4-4f3d-4ae2-9571-75675ad92bfb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		82dbf9c4-4f3d-4ae2-9571-75675ad92bfb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=82dbf9c4-4f3d-4ae2-9571-75675ad92bfb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		82dbf9c4-4f3d-4ae2-9571-75675ad92bfb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
````````````````````````````````````````````````````````````````````````

---

### Post by lindsay7 on 2009-07-09
Ok, thanks that is what I wanted to see.  Your hard drive was not mounted and that is why you could not get to the grub menu with the commands I gave you.

Anyway the grub menu is set to boot form sdc1 which is the 160gig hard drive and it will not do anything to your other drives.  If you want to start ubuntu you need to change the bios to start with the 160gig drive first and when you want to go back to raid you need to reset the bios to look at that drive set up first. Switching back and forth is a pain but it is just a couple of extra key strokes and no big deal. It will not hurt your system at all.

If you decide you want the grub menu to give you both options, I would post a new thread asking for help with a raid ubuntu/windows grub setup. I have never done it so I will not be much help.

---

### Post by NastyNative on 2009-07-09
ok thanks for clearing that up.

There should be a way to get the grub to load from sdc4
I assume that sdc1 means in bios terms sata 1 correct?

Ive been running vista on a raid for quite a while now and 
its just recently that I installed Ubuntu on my new drive 
which I installed into half of the 160GB WD drive.
So I only used about 80GB of the drive.

I thought All i had to do once I installed ubuntu and I was done with 
the partition.. it asked to load a bootloader to the primary "/" partition.

Once the grub loader is correctly working I will get a choice to 
either load vista or Ubuntu correct?

Thanks I just want to clear up a couple of things since im very 
new to ubuntu.

---

### Post by lindsay7 on 2009-07-09
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe80dce22

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 20023 160833536 7 HPFS/NTFS

[COLOR="Red"]Disk /dev/sdc: 160.0 GB, 16[/COLOR]0041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x540b8ddd

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 1216 9767488+ 83 Linux
/dev/sdc2 10199 19457 74366976 6 FAT16
/dev/sdc3 1217 10198 72147915 5 Extended
/dev/sdc5 7768 10198 19527007+ 83 Linux
/dev/sdc6 7524 7766 1951866 82 Linux swap / Solaris
/dev/sdc7 1217 7522 50652882 b W95 FAT32

Partition table entries are not in disk order
```

Sdc is the the third drive with Ubuntu installed, the astrick shown on sdc1 indicates that is the boot partition,

sda and sdb are the two drives where windows is installed and the raid drives. 

When you installed ubuntu it asked for a root partition this is the one that is desiganted "/".

The grub menu that you provided only shows the two versions of Ubuntu and memtest that can be booted by the grub menu. See below,

```
title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 82dbf9c4-4f3d-4ae2-9571-75675ad92bfb
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=82dbf9c4-4f3d-4ae2-9571-75675ad92bfb ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 82dbf9c4-4f3d-4ae2-9571-75675ad92bfb
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=82dbf9c4-4f3d-4ae2-9571-75675ad92bfb ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid 82dbf9c4-4f3d-4ae2-9571-75675ad92bfb
kernel /boot/memtest86+.bin
quiet
```

Window is not in this list so it can not be booted into.  Also, since windows and ubuntu are on different drives there would need to be mapping instructions to tell Ubuntu grub how to deal with the three drives.  These instructions can be added manually. But it would need to be done to account for the system using raid.  This is what I have no experience with at this time.

So as I said in the earlier post.  Windows will boot as it has been and if you want to load Ubuntu just change the bios to start from the 160gig dirve first.  Make a note of which drive is currently set up to be the first start drive and when you want to go back to the windows configuation, set it to start first.

One thing you may want to do to see how this looks graphically is to start Gparted or the partition editor that you will find under System/administration. This is the tool that is used to partition, repartition and make changes to the system drives.  It will show you how each drive is set up. You can change to each drive by clicking on the button on the top right corner of the window that you will see.

---

### Post by lindsay7 on 2009-07-09
Here is a screen shot of my drive for example (using Gparted)


[ATTACH]120539[/ATTACH]

---

### Post by dstew on 2009-07-11
Nasty, in your original post you said you installed the grub boot loader to the Ubuntu *partition*. This means you will not get a grub menu at boot-time, unless you configure the Vista boot loader to chainload the grub boot loader that you put in the partition.

Usually, to dual-boot, you put the grub boot loader into the Master Boot Record (MBR) of the disk, which is not a part of any partition. Then, when your BIOS goes to boot the disk, it will start grub, and not the Vista boot loader. In order to get the grub menu, you need to either get the Vista boot loader to chainload grub, or install grub to the MBR.

---

### Post by NastyNative on 2009-07-11
Device Boot Start End Blocks Id System
/dev/sdc1 * 1 1216 9767488+ 83 Linux
/dev/sdc2 10199 19457 74366976 6 FAT16
/dev/sdc3 1217 10198 72147915 5 Extended
/dev/sdc5 7768 10198 19527007+ 83 Linux
/dev/sdc6 7524 7766 1951866 82 Linux swap / Solaris
/dev/sdc7 1217 7522 50652882 b W95 FAT32


ok so according to this the * is where the boot loader is selected..
This is not the MBR???

How do i get the MBR to this drive and make it recognize the vista raid system???

This is the direction i Think Jeb was taking me too, installing the Raid drivers for ubuntu so that the MBR recognizes my vista Raid setup

---

### Post by dstew on 2009-07-12
> ok so according to this the * is where the boot loader is selected..
This is not the MBR???Actually, the * does not indicate where the boot loader is located. It is merely the partition boot flag, which is used by Windows system mostly to identify the system partition. Windows uses this flag to avoid booting a recovery partition, which may be located before the system partition on a particular disk. Linux, grub and the system BIOS ignore this flag.> How do i get the MBR to this drive and make it recognize the vista raid system???The MBR is the first sector of the disk, and is not part of any partition. It is only 512 bytes long, and so it cannot have very much in it. I usually contains the disk partition table, and a short bit of boot loader code. The boot loader is place by the BIOS into memory, and execution handed over to it. The boot loader loads another larger program from a partition file system, and hands execution over to that larger program. With grub, the small boot loader is stage1, and the larger program is stage2. When you install grub into the MBR, the installation command (setup (hd0) for example) causes the disk block address of the stage2 file to be embedded into the stage1 code, so that grub can load stage2. Grub stage1 cannot read a disk directory or search for stage2, so if you move your Linux partition, you would need to re-install grub.

Having said all that, your real question is whether or not you can boot your Vista RAID using grub. If your Vista system can be chainloaded, then grub can boot it. That is, if its structure is such that grub can load the first sector of the partition into memory, and transfer control to it, the rest should take care of itself. The grub menu command chainloader +1 attempts to do this. The problem arises because grub cannot deal with RAID filesystem partitions generally. It uses the BIOS to locate partitions, and a FakeRAID has BIOS extensions that generally grub cannot deal with. You might try the [dmraid way]("https://help.ubuntu.com/community/FakeRaidHowto") of installing grub, but generally people get confused with this. I do not know of any straightforward way to do it.

---

