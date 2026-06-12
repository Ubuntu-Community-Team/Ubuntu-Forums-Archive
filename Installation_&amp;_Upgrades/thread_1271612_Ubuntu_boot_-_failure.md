---
title: "Ubuntu boot - failure"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by cordlezz on 2009-09-21
Hey peeps. 

I have recently reinstalled Ubuntu 9.04 , 
and I'm dual-booting with Vista. 

When I boot, I get

"Try (hd0,0): Ext2:"

what does this mean?

Please help.

---

### Post by sideaway on 2009-09-21
Is this after you select which OS from GRUB? A little more information is needed.

It's most likely you've got your menu.lst setup wrongly.

---

### Post by cordlezz on 2009-09-21
After I reboot, I get into Windows bootloader, where I can choose between Vista and Ubuntu, and when I choose Ubuntu it takes a second, then the message shows up. 

If I do, 

sudo gedit /boot/grub/menu.lst 

the .lst is empty.

---

### Post by sideaway on 2009-09-21
Wait, so are you using Grub or the windows boot loader? I didn't think bootmgr could handle ext* partitions let alone even see linux installations.

---

### Post by cordlezz on 2009-09-21
It's the windows bootloader that pops up, I tried to restart with LiveCD and did a reinstall of Grub, 

sudo grub

find /boot/grub/stage 1
 then it returned (hd1,0)

then I did

root (hd1,0)

setup (hd1)
and the same message came up.

Then I tried setup (hd0) instead of (hd1)

then I got Grub 17 error

---

### Post by sideaway on 2009-09-21
Ok basically the only way I can see that post making sense is that you've misnamed Grub as the wondows boot loader and the menu.lst that you're looking at is off of a live CD?

EDIT: Was referring to the 2nd post. Can you please post the output of; sudo fdisk -l 

This will give me (and any other potential helper) an idea of the hard drive and partition structure.

---

### Post by cordlezz on 2009-09-21
I looked at the menu.lst from the liveCD, and it's empty

---

### Post by unmole on 2009-09-21
Boot into the live CD and do a

             sudo grub-install /dev/hda

---

### Post by sideaway on 2009-09-21
Yes it would be, can you please post the output of sudo fdisk -l as above.

I generally you type setup(hd0) as this will install GRUB to the MBR of your primary HDD, as this is disk on which the bios searches for a boot manager. The root hd(0,1) is where the grub files will be located (such as your menu.lst)

Also try setup (hd0,0)

---

### Post by cordlezz on 2009-09-21
Here is my output from sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6059

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    5  Extended
/dev/sda2   *       38914       77827   312571904    7  HPFS/NTFS
/dev/sda5           37438       38913    11855938+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040e9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37459   300889386   83  Linux
/dev/sdb2           37460       38913    11679255    5  Extended
/dev/sdb5           37460       38913    11679223+  82  Linux swap / Solaris

---

### Post by cordlezz on 2009-09-21
Should I try ..



             sudo grub-install /dev/hda  .. ?

---

### Post by cordlezz on 2009-09-21
Should I try 


             sudo grub-install /dev/hda ?

---

### Post by cordlezz on 2009-09-21
> **unmole said:**
> Boot into the live CD and do a

             sudo grub-install /dev/hda


This is what I get 

ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/hda: Not found or not a block device.

---

### Post by presence1960 on 2009-09-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by cordlezz on 2009-09-21
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


I'm new to Linux-world.

I have downloaded your file, how do I install it?

apt-get ?

---

### Post by presence1960 on 2009-09-21
> **cordlezz said:**
> I'm new to Linux-world.

I have downloaded your file, how do I install it?

apt-get ?

put the file on the desktop. Then go Applications > Accessories > Terminal. When the terminal opens copy & paste this command in the terminal:
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 

press enter. it will ask for your password. type your password- you will not see any characters when typing password in terminal, that is for security reasons. When the process is complete you will find a RESULTS.txt file on your desktop. Post the entire contents of that file back here please.

---

### Post by cordlezz on 2009-09-21
Here is the result.txt

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e6059

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   625,137,344   625,137,282   5 Extended
/dev/sda5         601,425,468   625,137,344    23,711,877  82 Linux swap / Solaris
/dev/sda2    *    625,137,664 1,250,281,471   625,143,808   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00040e9c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   601,778,834   601,778,772  83 Linux
/dev/sdb2         601,778,835   625,137,344    23,358,510   5 Extended
/dev/sdb5         601,778,898   625,137,344    23,358,447  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: TYPE="swap" UUID="7de5c967-2f3f-4722-8ac0-470d5c7a7ab9" 
/dev/sdb1: UUID="4afd0222-990e-42e6-8d9b-e13bc260b519" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="686727fb-ec4b-4e8d-840d-32e241a64779" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4afd0222-990e-42e6-8d9b-e13bc260b519 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4afd0222-990e-42e6-8d9b-e13bc260b519

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4afd0222-990e-42e6-8d9b-e13bc260b519
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4afd0222-990e-42e6-8d9b-e13bc260b519 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4afd0222-990e-42e6-8d9b-e13bc260b519
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4afd0222-990e-42e6-8d9b-e13bc260b519 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4afd0222-990e-42e6-8d9b-e13bc260b519
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e9c7ca82-9c88-454b-a18d-0303e0ae0af5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e9c7ca82-9c88-454b-a18d-0303e0ae0af5 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=4afd0222-990e-42e6-8d9b-e13bc260b519 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=686727fb-ec4b-4e8d-840d-32e241a64779 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 120.2GB: boot/grub/menu.lst
 120.2GB: boot/grub/stage2
 120.1GB: boot/initrd.img-2.6.28-11-generic
 120.2GB: boot/vmlinuz-2.6.28-11-generic
 120.1GB: initrd.img
 120.2GB: vmlinuz

---

### Post by presence1960 on 2009-09-21
your vista partition is unmountable. You can try to run recovery console from the Vista DVD. Follow the instructions for vista [here]("http://ubuntuforums.org/showthread.php?t=1014708"), **but first set your Vista disk to boot first in BIOS in the hard disk boot order.**

Follow the instructions for vista on that link. Reboot and see if you boot right into Vista. if so reboot and go in BIOS again and make the sdb disk first in hard disk boot order. This will bring up GRUB menu when you boot. Boot into ubuntu, open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```

scroll to the bottom and remove these entries:
```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e9c7ca82-9c88-454b-a18d-0303e0ae0af5 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e9c7ca82-9c88-454b-a18d-0303e0ae0af5 ro single
initrd /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title Ubuntu 9.04, memtest86+ (on /dev/sda6)
root (hd0,5)
kernel /boot/memtest86+.bin
savedefault
boot
```

Add this 

```
title          Windows Vista
rootnoverify   (hd1,1)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

Click Save on the toolbar, close file & reboot.

---

### Post by cordlezz on 2009-09-21
I followed the Vista steps 2 times, but when I reboot, I automatically load into Windows Boot Manager, where I can see Windows Vista and Ubuntu as choices.

wtf is wrong ?

---

### Post by presence1960 on 2009-09-21
> **cordlezz said:**
> I followed the Vista steps 2 times, but when I reboot, I automatically load into Windows Boot Manager, where I can see Windows Vista and Ubuntu as choices.

wtf is wrong ?

Now you need to read my instructions on my last post. I asked you to boot into windows after doing what you just did. Choose windows from the menu and see if Vista boots. if it does reboot and follow the rest of my instructions. You only did half of what I suggested you to do.

P.S. That Ubuntu option on the windows bootloader is left over from your wubi install. I don't know what file you need to edit to get rid of it. In XP you edit the boot.ini file to remove the Ubuntu entry.

---

### Post by presence1960 on 2009-09-21
> **cordlezz said:**
> I followed the Vista steps 2 times, but when I reboot, I automatically load into Windows Boot Manager, where I can see Windows Vista and Ubuntu as choices.

wtf is wrong ?

of course you are going to go directly into vista bootloader you just repaired vista and put it's bootloader on the MBR of sda. Now reboot & put sdb as first in the hard disk boot order in BIOS. sdb has GRUB on it's MBR. Follow the rest of my instructions that you did not do.

---

### Post by cordlezz on 2009-09-21
I was able to boot into Vista after doing bootrec.exe /fixboot and /fixmbr ..

but how do i recognize the sdb disc ? 

I have tried to change the 2 disc's i have in the boot-order-menu

---

### Post by presence1960 on 2009-09-21
> **cordlezz said:**
> I was able to boot into Vista after doing bootrec.exe /fixboot and /fixmbr ..

but how do i recognize the sdb disc ? 

I have tried to change the 2 disc's i have in the boot-order-menu

That I can't help you with. You need to figure out which one is which. if you only have 2 hard disks and you are getting the windows bootloader on boot, then try switching since GRUB is on MBR of that other disk

---

### Post by cordlezz on 2009-09-23
> **presence1960 said:**
> That I can't help you with. You need to figure out which one is which. if you only have 2 hard disks and you are getting the windows bootloader on boot, then try switching since GRUB is on MBR of that other disk


I'm using the same partition for Ubuntu as I use with Vista. I have only 1 HD, and if I try to run that through BIOS, I only get Windows Boot Loader, no grub.

---

### Post by presence1960 on 2009-09-23
> **cordlezz said:**
> I'm using the same partition for Ubuntu as I use with Vista. I have only 1 HD, and if I try to run that through BIOS, I only get Windows Boot Loader, no grub.

how can you say you only have one hard drive when the output from your boot info script shows you clearly have two 320 GB drives.

And **again I will repeat** you need to follow the last half of my instructions in post # 18 so when you boot GRUB will come up. Currently you have Vista on MBR because you repaired Vista, now you need to change the first disk that boots in BIOS to sdb (the one with Ubuntu on it). Then follow my directions to add a Vista entry to GRUB menu.

if you aren't going to do that I won't be able to help.

P.S. Vista is on sda2 and ubuntu is on sdb1. they are two separate hard disks. Also it is impossible to have Ubuntu & Vista on the same partition. But it is possible to have Ubuntu & Vista on the same disk. But this is not the case here- you have 2 320 GB hard disks & Vista is on one & Ubuntu is on the other disk.

---

### Post by rreese6 on 2009-09-23
> **cordlezz said:**
> I'm using the same partition for Ubuntu as I use with Vista. I have only 1 HD, and if I try to run that through BIOS, I only get Windows Boot Loader, no grub.

Cordlezz,

I do not want to interrupt this thread because I think the helper is doing a very fine job, However, since Cordlezz is new to linux, I just wanted to give him a better understanding of why there appears to be two hard drives.

I does appear to me that you have 2 hard drives. This is obvious from the command "fdisk -l" that you did. The drives are Identified in Linux by their device name. You will see one says "/dev/sda" and the other one says "/dev/sdb". You will also notice the Disk identifier: 

Disk identifier: 0x000e6059 is for the first drive (/dev/sda)
Disk identifier: 0x00040e9c is for the second drive (/dev/sdb)

Follow the instructions that Presence1960 is giving you and you will be very happy. Do try "other" suggestions as that might mess up the whole thing.

Presence1960: Do you think it might be wise for him to attempt a lilo removal on /dev/sda before the grub-install on /dev/sda? I am not sure how that can co-exist with the Windows Bootloader, but it does appear in the diagnostic list.

---

### Post by presence1960 on 2009-09-23
> **rreese6 said:**
> 

Presence1960: Do you think it might be wise for him to attempt a lilo removal on /dev/sda before the grub-install on /dev/sda? I am not sure how that can co-exist with the Windows Bootloader, but it does appear in the diagnostic list.

Actually Lilo should be gone now. His Vista is on sda2 and if you look at the boot info script output sda2 was unmountable. So I had him repair Vista using the Vista DVD recovery console. That put Vista on sda's MBR which is why he boots into Vista now. I want him to switch boot order in BIOS to sdb because GRUB is already installed on MBR of sdb. This way when he boots GRUB will come up. Then I explained to him to edit menu.lst to add the Vista entry to GRUB menu.

It seems he can't get past the point of recognizing he has 2 hard disks and they are separate entities. he thinks Vista & Ubuntu are on the same disk.

It is all outlined in simple instructions in post #18 of this thread.

P.S. you are not interrupting. maybe you can explain it differently than I so maybe the OP will grasp the concepts.

---

