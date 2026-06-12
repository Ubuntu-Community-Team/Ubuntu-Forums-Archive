---
title: "GRUB, Restore, Repartition, Reinstall, Boot Problem, Ubuntu 8.04.2"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Buggin1965 on 2009-03-11
Problem:
GRUB will not boot. And after trying many different solutions I cannot figure out how to fix it. I do not know much about how GRUB works or how the MBR works but I am learning.  I keep getting ERROR 22: No Such partition at startup.
Then I get a list of Ubuntu 8.04.2 profiles.
ubuntu 8.04.2, kernel 2.6.24-23-generic
ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
repeated 6 times
ubuntu 8.04.2, memtest86+

Pressing "e" shows:
```
root (hd0,0)
kernel /vmlinuz-2.6.24.-23-generic root=UUID=02bb8244-73f1-433a-ad44-->
initrd /initrd.img-2.6.24-23-generic
quiet
```

pressing "e" again allows me to edit the first line and I change it to:
root (hd0,0)
then pressing "b" starts the boot process with the orange sliding bar then throws an error and exits to a shell.
check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/02bb8244-73f1-433a-ad44-1daa207592cd does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

UPDATE:
I manually edited the GRUB menu.lst file and now I have access to the system.  But I get fsck unable to mount errors.  Now I need to know how to make the stable system.

terminal command: "df -h" does not list any of the partitions that should be there. example /dev/sda1 which should be /boot or /dev/sda3 which should be /


-------------------------------------
Background:
I have an Ubuntu machine that ran out of space on the /boot partition and the /root partition.  I used tar and this command to perform a backup of the system to an external hard drive.
```
sudo tar cvpzf /media/serverback2/2009_0306_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/media/serverback2/2009_0306_backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /
```

Attempt to Resize Partitions:
Then I used the gparted live CD to try and resize the partitions.  The repartition process failed leaving me with a corrupted disk.

Restore Attempts:
1) Reinstall Ubuntu 8.04.2
I reinstalled ubuntu 8.04.2 to get a bootable machine and partition the drive properly.  Then I restored the backup TAR file using:
 ```
tar xvpfj /media/serverback2/2009_0306_backup.tgz -C /

```
This process replaced all of the files as expected. Unfortunately it also replaced the /boot files.  When I restart I get ERROR 22 .

2) I found this post ( [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ) through google and tried the following procedures (none of them solved my problem): Quick Start, Super GRUB Disk, preparing your working environment, Recovering GRUB Automatically, Using the Ubuntu Alternate CD and "The GUI way", manually editing GRUB let me boot with errors and a system that is unstable.

3) Super GRUB Disk live CD v .97
I get a menu with a list of the same profiles that do not work.
ubuntu 8.04.2, kernel 2.6.24-23-generic
ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
repeated 6 times
ubuntu 8.04.2, memtest86+

When using the Super GRUB Disk to point the boot loader to (hd0,0) I get the following error:
```
check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uued/02bb8244-73f1-433a-ad44-1daa207592cd does not exist. Dropping to a shell!
```

4)  I tried using the Alternate CD in rescue mode and GUI install mode. Both failed

5) Using the live CD tried to manually edit the "menu.lst" file:
root (hd0,0)
and changed the kernel to point to = /dev/sda3 instead of UUID="a bunch of numbers"

It looked like it might work then I received:
```
fsck.ext2: unable to resolve 'UUID=ab1d7c93-7256-4c8a-8d23-9a772a462308'
fsck.ext3: unable to resolve 'UUID=13435552-884b-424a-a39e-a0add6ddcd6'
fsck died with exit status 8

File system check failed.
```

I press "control d" and I get the same unable to mount the above partitions

Then I am prompted with a login.  I enter the the login and now I have access to the system.  But I need to make the system stable.

The partitions are not mounted properly.  when I run "df -h" it does not list the partitions for "/boot" or "/"


-----------------------------------
Original Structure:
sda1   /boot   200MB
sda2   swap    4 GB
sda3     /         30GB
sda4   /home  ~1.2TB


New Structure:
/dev/sda1   /boot  500MB
/dev/sda2   swap   4GB
/dev/sda3    /     ~1.4TB

--------------------------------------
System Specs:
Ubuntu 8.04.2 i386
3ware RAID5 controller with four 500GB Disks
2 GB RAM
Intel Core 2 2.4GHz
ASUS P5B-VM
SATA DVD drive
Floppy Drive

---------------------------------------
Information that I found:
I think that GRUB should be here:
IDE     SCSI    Grub
hda1    sda1   (hd0,0)

find /grub/stage1  RETURNS  (hd0,0)


---------------------------------------
Questions:
1. Do I have to use the same Ubuntu installer CD version as the original OS version?
2. Does the TAR file remember which partition to restore the files to?
3. Is there a way to exclude directories inside of the TAR from being extracted? 
3. When I load the ubuntu live CD it is showing the 500mb BOOT partition in the /media folder and I cannot find the / (root) partition.  When I run "fdisk -l" I do not get any results. Why?
4. Installed ububtu 8.04.2 again and copied the /boot folder to a USB drive.  Can I copy the pre-install file to the post TAR restore folder and get it to work?
5. I also copied the MBR pre-TAR restore using: dd if=/dev/hda1 of=/media/usbstick/mbr-bkp bs=512 count=1 . Will restoring the MBR fix my problem?
6. Am I going about this the wrong way?

I am grateful for any help that I can get.
Thank you.

---

### Post by meierfra. on 2009-03-11
In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD,  download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by adrian15 on 2009-03-13
> **Buggin1965 said:**
> 
When using the Super GRUB Disk to point the boot loader to (hd0,0) I get the following error:
```
check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uued/02bb8244-73f1-433a-ad44-1daa207592cd does not exist. Dropping to a shell!
```


If your system does not have too many problems (fstab being incorrect) you can boot it with Super Grub Disk but you are not using the correct option.

You should use the Boot Linux Directly option from the **Choose SGD Language & Help -> GNU/Linux** menu.

In old SGD versions you will find:
Boot Linux
Boot Linux Directly 
choose: Boot Linux Directly

In new SGD versions you will find:
Boot Linux
Boot Linux Indirectly
choose: Boot Linux.

adrian15

---

### Post by Buggin1965 on 2009-03-16
I booted from the live CD then downloaded and ran the Boot info script, here are the results:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 384065 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 384065 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1499.9 GB, 1499968045056 bytes
255 heads, 63 sectors/track, 182360 cylinders, total 2929625088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000243fc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       979,964       979,902  83 Linux
/dev/sda2             979,965     8,787,554     7,807,590  82 Linux swap / Solaris
/dev/sda3           8,787,555 2,929,613,399 2,920,825,845  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d0b3038f-5434-49ce-b111-96dbf8987ec3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="3c635802-98ba-4d4b-9d82-d1aa6954c9e6" 
/dev/sda3: UUID="4bb9a289-b57b-4612-a5fd-951555ef8b6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================= sda1/grub/menu.lst: =============================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

fallback 1 #The entry which should be booted in the event of the first one failing

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
# kopt=root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/sda3
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro quiet splash
initrd		/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-20-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-20-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro quiet splash
initrd		/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-20-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro single
initrd		/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.2, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-17-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro quiet splash
initrd		/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-17-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro single
initrd		/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/menu.lst
    .1GB: grub/stage2
    .0GB: initrd.img-2.6.24-23-generic
    .2GB: initrd.img-2.6.24-23-generic.bak
    .0GB: vmlinuz-2.6.24-23-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02bb8244-73f1-433a-ad44-1daa207592cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=ab1d7c93-7256-4c8a-8d23-9a772a462308 /boot           ext2    defaults        0       2
# /dev/sda7
UUID=13435552-884b-424a-a39e-a0add6dc5cd6 /home           ext3    defaults        0       2
# /dev/sda5
UUID=82c707a0-2f9a-4a25-b6ae-95c7eed759d5 none            swap    sw              0       0

#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



```

I want to point out the manual changes that I have made to the menu.lst which may help you figure out what I am doing wrong.

Changed fist root entry:
From: root (hd0,5)  (which was correct for the original partition structure)
TO: root (hd0,0)

Changed Kernel Location
From: root=UUID=02bb8244-73f1-433a-ad44-1daa207592cd ro quiet splash
TO: root=/dev/sda3

-------------------
I hope this information will help you, help me.  Now I am going to try the SGD again using adrian15 instructions.

Thank You.

---

### Post by meierfra. on 2009-03-16
Your problem is in "/etc/fstab". All the UUID's are wrong.  You can find the correct UUID's in the "blkid" section of "RESULTS.tex" or by running "sudo blkid".  Let me know if you need help reconfiguring "fstab"


Grub seems to be configured correctly by now.  Although I still recommend some changes:

At "ro" to the kernel line of the Ubuntu item.

Change "#groot (hd0,5)" to "#groot (hd0,0)"

Change the "Ubuntu (recovery mode)" the same way you changed the Ubuntu item.


If you are using "hibernation" or want a "splash" screen during boot up, you also need to mess with the "UUID" of your swap space. But lets worry about that once you are able to boot into Ubuntu.

---

### Post by Buggin1965 on 2009-03-16
Ok, I booted to the SGD and selected:
Boot Linux then boot gnu/linux directly and I get this error:
```
findf /etc/fstab
fstabroot (hd0,2)/etc/fstab
No root string was found on selected fstab file.
Dropping error 15.

Error 15: File not found
Press any key to continue

```

Then I went back to the Super BRUB disk menu and selected the "Automatically fix GRUB" option and rebooted the system. GRUB passes stage1 and stage2, but I receive this message while the system is starting up.
```

One can change the type of al the mounts in a mount subtree containing the directory dir:
  mount --make-rshared dir
  mount --make-rslave dir
  mount --make-rprivate dir
  mount --make-runbinable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom, or by label, using -l label or by uuid, using -u uuid. Other options: [-nfFrsvw] [-o options] [-p passwords].

For many more details, say man 8 mount.

*checking file systems..
fsck 1.40.8 (13-mar-2008)
fsck.ext2: unable to resolve 'UUID=ab1d7c93-7256-4c8a-8d23-9a772a462308'
fsck.ext3: Unable to resolve 'UUID=13435552-884b-424a-a39e-a0add6dc5cd6'
fsck died with exit status 8

* File System check failed.
A log is being saved in /var/log/fsck/checkfs is that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.
CONTROL-D wil terminate this shell and resume system boot.
Give root password for maintenance (or type Control-D to continue):
*Stopping NTP server ntpd
*starting NTP server ntpd

```

Pressing control-d give a few more errors about not being able to mount the disks that I was unable to see long enough to write down.

I checked the fsck log file. Here is the output:
```

Log of fsck -C -R -A -a
Mon Mar 16 12:21:28 2009

fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Unable to resolve 'UUID=ab1d7c93-7256-4c8a-8d23-9a772a462308'
fsck.ext3: Unable to resolve 'UUID=13435552-884b-424a-a39e-a0add6dc5cd6'
fsck died with exit status 8

Mon Mar 16 12:21:28 2009
----------------

```

Per Meierfa's suggestion I have altered the fstab. Here is a copy of the changes that I have made:

Original
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02bb8244-73f1-433a-ad44-1daa207592cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=ab1d7c93-7256-4c8a-8d23-9a772a462308 /boot           ext2    defaults        0       2
# /dev/sda7
UUID=13435552-884b-424a-a39e-a0add6dc5cd6 /home           ext3    defaults        0       2
# /dev/sda5
UUID=82c707a0-2f9a-4a25-b6ae-95c7eed759d5 none            swap    sw              0       0

#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```


Modified fstab (does not function properly)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d0b3038f-5434-49ce-b111-96dbf8987ec3 /boot               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=3c635802-98ba-4d4b-9d82-d1aa6954c9e6 none           swap    sw        0       2
# /dev/sda3
UUID=4bb9a289-b57b-4612-a5fd-951555ef8b6a /            ext3    sw              0       0

#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Now I receive a new error after saving the changes and rebooting. While booting it makes it past the mounting of the disks, however I can see errors flying by on the screen while booting.  It finally stops at a blue and gray screen the displays the following:
```

Could not start the X
server (your graphical environment) due to some internal error. Please contact you system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.

```

Pressing Enter does nothing and rebooting stops in the same window.

During boot up I receive the following errors:
```

* Activating swap... [OK]
[78.234323] EXT3-fs: Unrecognized mount option "sw" or missing value
[78.235467] EXT3-fs: Unrecognized mount option "sw" or missing value
mount: / not mounted already, or bad option

*checking file systems....
fsck 1.40.8 (13-Mar-2008)
/dev/sda1: Clean, 70/1228800 files, 151573/489948 blocks [ok]

*Mounting local filesystems...
mount: No medium found [fail]

[355.718494] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-care.c: couldn't find an input interrupt endpoint 

```

Looks like the system can only read files and directories. I see a lot of "No such file or directory" and "Read-only file system"

Then a lot service fail to start running:
clamav


Looks like I have screwed up the fstab file.  How can I change the fstab now that I cant boot again?

What should <dump> and <pass> in the fstab be set to for /boot and /  ?

Thank You

---

### Post by meierfra. on 2009-03-16
Change the "sw" in 

> # /dev/sda3
UUID=4bb9a289-b57b-4612-a5fd-951555ef8b6a /            ext3    sw              0       0




to "defaults, errors=remount-ro"

---

### Post by Buggin1965 on 2009-03-16
Worked!!! Awesome, Thank You!

---

### Post by meierfra. on 2009-03-16
> Worked!!!

Great. Have fun with Ubuntu.

---

