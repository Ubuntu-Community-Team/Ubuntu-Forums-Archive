---
title: "cannot find find my boot loader after reinstall xp"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by seuzo on 2009-09-08
hi,

Here the story. Am using a laptop
At first Win xp and ubuntu 9.04 dual boot fine.
for some reason win xp got problem after using my laptop to do some recover on a DVD disc.But still can boot into ubuntu 9.04.

so i reinstall window xp did not think that window xp boot will overwrite my grub boot loader because is late at night could not think. Now after that install. boot only into window. i check my partition everything is still there. 

How to reinstall my boot loader so i can dual boot again?
I do not wish to reinstall my ubuntu partition after setting up my mobile broadband and virualbox. 

any experts can help on boot loader problem?

---

### Post by presence1960 on 2009-09-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by drs305 on 2009-09-09
This may help - from the Ubuntu wiki:
[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by seuzo on 2009-09-09
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

```
[CODE]=======

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ca00ca0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sda2          83,891,430   123,893,279    40,001,850  83 Linux
/dev/sda3         123,893,280   131,893,649     8,000,370   5 Extended
/dev/sda5         123,893,343   131,893,649     8,000,307  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6C74F39874F362EE" TYPE="ntfs" 
/dev/sda2: UUID="15cd7310-b24c-42e5-a15c-01a1ad993208" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9d471c50-8f49-470b-9311-798afa3d84a9" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		10

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
# kopt=root=UUID=15cd7310-b24c-42e5-a15c-01a1ad993208 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=15cd7310-b24c-42e5-a15c-01a1ad993208

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
## update-grub will ignore non-xen
```


Hope this can help me?

---

### Post by presence1960 on 2009-09-09
well you left out the bottom half of the results.txt file. Barring any irregularities this should do the trick:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In #6 use setup (hd0)**

```
Boot into ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in menu.lst
Scroll down to this line: ### END DEBIAN AUTOMAGIC KERNELS LIST

Skip 1 line and make sure your windows entry reads like this:

title          Windows XP
rootnoverify   (hd0,0)
chainloader    +1

---

### Post by presence1960 on 2009-09-09
```
title         Windows XP
rootnoverify  (hd0,0)
chainloader   +1
```

that is how it should look in menu.lst for windows entry

---

### Post by seuzo on 2009-09-09
> **presence1960 said:**
> well you left out the bottom half of the results.txt file. Barring any irregularities this should do the trick:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In #6 use setup (hd0)**

```
Boot into ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in menu.lst
Scroll down to this line: ### END DEBIAN AUTOMAGIC KERNELS LIST

Skip 1 line and make sure your windows entry reads like this:

title          Windows XP
rootnoverify   (hd0,0)
chainloader    +1



```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		15cd7310-b24c-42e5-a15c-01a1ad993208
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=15cd7310-b24c-42e5-a15c-01a1ad993208 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		15cd7310-b24c-42e5-a15c-01a1ad993208
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=15cd7310-b24c-42e5-a15c-01a1ad993208 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		15cd7310-b24c-42e5-a15c-01a1ad993208
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=15cd7310-b24c-42e5-a15c-01a1ad993208 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		15cd7310-b24c-42e5-a15c-01a1ad993208
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=15cd7310-b24c-42e5-a15c-01a1ad993208 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		15cd7310-b24c-42e5-a15c-01a1ad993208
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=15cd7310-b24c-42e5-a15c-01a1ad993208 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d471c50-8f49-470b-9311-798afa3d84a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  62.0GB: boot/grub/menu.lst
  62.1GB: boot/grub/stage2
  62.0GB: boot/initrd.img-2.6.28-11-generic
  62.0GB: boot/initrd.img-2.6.28-15-generic
  62.0GB: boot/vmlinuz-2.6.28-11-generic
  62.1GB: boot/vmlinuz-2.6.28-15-generic
  62.0GB: initrd.img
  62.0GB: initrd.img.old
  62.1GB: vmlinuz
  62.0GB: vmlinuz.old
```

---

### Post by seuzo on 2009-09-09
Hi, thank you. so is better to install in my MBR? am i right?

---

### Post by presence1960 on 2009-09-09
If you want the GRUB menu to come up and give you the choice of Ubuntu or XP it has to be in MBR.

---

