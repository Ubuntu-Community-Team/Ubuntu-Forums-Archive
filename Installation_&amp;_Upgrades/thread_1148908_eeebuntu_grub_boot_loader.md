---
title: "eeebuntu grub boot loader"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by MrCracker on 2009-05-04
I have a eee pc with 2 ssd's : here is my fdisk -l from ubuntu:

```
Disk /dev/sda: 4034 MB, 4034838528 bytes
16 heads, 63 sectors/track, 7818 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x437a52ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7818     3940240+  83  Linux

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1874    15052873+  83  Linux
/dev/sdb2            1875        1962      706860    5  Extended
/dev/sdb5            1875        1962      706828+  82  Linux swap / Solaris

```

Ubuntu is installed on the sdb disk and backtrack is installed on the sda disk.

I would like to add backtrack to the boot menu of grub so i have an option of loading it up when i boot.

This is my current /boot/grub/menu.lst file:

```
title		Ubuntu 8.10, kernel 2.6.27-8-eeepc
uuid		65c68579-dc80-47fe-b761-f062e9cf520d
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=65c68579-dc80-47fe-b761-f062e9cf520d ro quiet splash clocksource=hpet 
initrd		/boot/initrd.img-2.6.27-8-eeepc
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc (recovery mode)
uuid		65c68579-dc80-47fe-b761-f062e9cf520d
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=65c68579-dc80-47fe-b761-f062e9cf520d ro  single
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		Ubuntu 8.10, memtest86+
uuid		65c68579-dc80-47fe-b761-f062e9cf520d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Normal Boot (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Perform Disk Scan (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Restore Factory Settings (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y 
initrd		/boot/initramfs-eeepc.img
savedefault
boot

```

Now to add backtrack, I'm adding the following.. which is obviously wrong because it shows up as error 15: file not found or something like that..

title		Backtrack 3
root            (hd0,0)
kernel		/boot/vmlinuz ro /dev/hdc1 vga = 773
initrd		/boot/splash.initrd
quiet

whats wrong with the above? im guessing its the root .. i can't figure out how to point it to the first ssd "sda" .. help me out? :D

---

### Post by caljohnsmith on 2009-05-04
In order to boot Backtrack, it would help to first get some more info about your setup related to booting, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup.

John

---

### Post by MrCracker on 2009-05-04
Here it is:

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
                       [1;31m================================================
                       ===============================[0;39m [1;31m Welcome 
                       to BackTrack 3 Final [0;39m 
                       [1;31m================================================
                       ===============================[0;39m [1;29mThe 
                       system is up and running now.[0;29m Login as 
                       "[1;29mroot[0;29m" with password 
                       "[1;29mtoor[0;29m", both without quotes, lowercase. 
                       [1;29mAfter you login, try the following 
                       commands:[0;29m mc ....... to start Midnight 
                       Commander (edit/copy/move/create/delete files) startx 
                       ... to run Xwindow system with KDE in VESA mode 
                       1024x768 at 75Hz xconf .... to autoconfigure your 
                       graphics card for better performance [1;29mOther 
                       commands you may find useful (for experts 
                       only!):[0;29m uselivemod ... to insert (install) Slax 
                       module into the system on the fly mkfileswap ... to 
                       create a special file on your harddisk for swapping 
                       mkchanges .... to create a special file on your 
                       disk/USB to save Slax changes [1;31m When finished, 
                       use "poweroff" or "reboot" command and wait until it 
                       completes [0;39m 
                       [1;31m================================================
                       ===============================[0;39m
    Boot files/dirs:   /etc/fstab /etc/lilo.conf /boot/map

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

Disk /dev/sda: 4034 MB, 4034838528 bytes
16 heads, 63 sectors/track, 7818 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x437a52ed

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,880,543     7,880,481  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf26d47c4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    30,105,809    30,105,747  83 Linux
/dev/sdb2          30,105,810    31,519,529     1,413,720   5 Extended
/dev/sdb5          30,105,873    31,519,529     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5e7a983c-6f9c-405f-8cef-d8d58fa04b76" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="65c68579-dc80-47fe-b761-f062e9cf520d" TYPE="ext3" 
/dev/sdb5: UUID="5ccd5362-cdff-4769-abfa-b8c397012f01" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)


=============================== sda1/etc/fstab: ===============================

aufs / aufs defaults 0 0 # AutoUpdate
devpts /dev/pts devpts gid=5,mode=620 0 0 # AutoUpdate
proc /proc proc defaults 0 0 # AutoUpdate
sysfs /sys sysfs defaults 0 0 # AutoUpdate
/dev/hdc1 /mnt/hdc1 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/hdd1 /mnt/hdd1 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/hdd5 /mnt/hdd5 swap auto,defaults 0 0 # AutoUpdate
/dev/sda1 /mnt/sda1 vfat auto,noatime,users,suid,dev,exec,quiet,umask=0,check=s,shortname=mixed 0 0 # AutoUpdate
/dev/fd0 /mnt/floppy vfat noauto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
tmpfs /tmp tmpfs defaults,noatime,mode=0777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=0777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0777 0 0

============================= sda1/etc/lilo.conf: =============================

#Backtrack

lba32
boot = /dev/hdc
prompt
timeout = 60
change-rules
reset
vga = 773
image = /boot/vmlinuz
root = /dev/hdc1
label = Back|track3


#ubuntu
other = /dev/hdd2
label = ubuntu
table = /dev/hdd
=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/vmlinuz

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
# kopt=root=UUID=65c68579-dc80-47fe-b761-f062e9cf520d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=65c68579-dc80-47fe-b761-f062e9cf520d

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
# defoptions=quiet splash clocksource=hpet

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

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc
uuid		65c68579-dc80-47fe-b761-f062e9cf520d
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=65c68579-dc80-47fe-b761-f062e9cf520d ro quiet splash clocksource=hpet 
initrd		/boot/initrd.img-2.6.27-8-eeepc
quiet

title		Backtrack 3
root            (hd1,1)
kernel		/boot/vmlinuz ro /dev/hdc1 vga = 773
initrd		/boot/splash.initrd
quiet


title		Ubuntu 8.10, kernel 2.6.27-8-eeepc (recovery mode)
uuid		65c68579-dc80-47fe-b761-f062e9cf520d
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=65c68579-dc80-47fe-b761-f062e9cf520d ro  single
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		Ubuntu 8.10, memtest86+
uuid		65c68579-dc80-47fe-b761-f062e9cf520d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Normal Boot (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Perform Disk Scan (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Restore Factory Settings (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y 
initrd		/boot/initramfs-eeepc.img
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=65c68579-dc80-47fe-b761-f062e9cf520d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5ccd5362-cdff-4769-abfa-b8c397012f01 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/menu.lst
   4.7GB: boot/grub/stage2
   4.7GB: boot/initrd.img-2.6.27-8-eeepc
   4.7GB: boot/vmlinuz-2.6.27-8-eeepc
   4.7GB: initrd.img
   4.7GB: vmlinuz

---

### Post by caljohnsmith on 2009-05-04
How about trying the following entry in your Grub's menu.lst to boot Backtrack:
```
title Backtrack 3
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Let me know if that works or not, and if not, what the error is. We can work from there if necessary.

John

---

### Post by MrCracker on 2009-05-04
Hey caljohnsmith, thanks for the help so far.

I updated my menu.lst file to what you told me and I booted up the pc, selected backtrack from the list and this is what I got:

Starting up...
L 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99  And a bunch more 99's ... 

weird lol

So then I set my ubuntu disk as the main disk on startup, it was second before.. and booted it up.. same thing.

Any ideas?

---

### Post by MrCracker on 2009-05-05
I reinstalled eeebuntu cuz i killed it with an update. Anyways it added backtrack to other automaticlly.. but when I go to it i get an error 15: file not found or something like that... im not sure if that changes anything so i will run the script again and post the results


menu.lst file: 

```
title		Ubuntu 8.10, kernel 2.6.27-8-eeepc
uuid		8a7a4042-9fec-44b4-8980-ec636f66d2c7
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=8a7a4042-9fec-44b4-8980-ec636f66d2c7 ro quiet splash clocksource=hpet 
initrd		/boot/initrd.img-2.6.27-8-eeepc
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc (recovery mode)
uuid		8a7a4042-9fec-44b4-8980-ec636f66d2c7
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=8a7a4042-9fec-44b4-8980-ec636f66d2c7 ro  single
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		Ubuntu 8.10, memtest86+
uuid		8a7a4042-9fec-44b4-8980-ec636f66d2c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Back|track3 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdc1 vga = 773 
savedefault
boot

```

results

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
                       [1;31m================================================
                       ===============================[0;39m [1;31m Welcome 
                       to BackTrack 3 Final [0;39m 
                       [1;31m================================================
                       ===============================[0;39m [1;29mThe 
                       system is up and running now.[0;29m Login as 
                       "[1;29mroot[0;29m" with password 
                       "[1;29mtoor[0;29m", both without quotes, lowercase. 
                       [1;29mAfter you login, try the following 
                       commands:[0;29m mc ....... to start Midnight 
                       Commander (edit/copy/move/create/delete files) startx 
                       ... to run Xwindow system with KDE in VESA mode 
                       1024x768 at 75Hz xconf .... to autoconfigure your 
                       graphics card for better performance [1;29mOther 
                       commands you may find useful (for experts 
                       only!):[0;29m uselivemod ... to insert (install) Slax 
                       module into the system on the fly mkfileswap ... to 
                       create a special file on your harddisk for swapping 
                       mkchanges .... to create a special file on your 
                       disk/USB to save Slax changes [1;31m When finished, 
                       use "poweroff" or "reboot" command and wait until it 
                       completes [0;39m 
                       [1;31m================================================
                       ===============================[0;39m
    Boot files/dirs:   /etc/fstab /etc/lilo.conf /boot/map

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

Disk /dev/sda: 4034 MB, 4034838528 bytes
16 heads, 63 sectors/track, 7818 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x437a52ed

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,880,543     7,880,481  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf26d47c4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    30,105,809    30,105,747  83 Linux
/dev/sdb2          30,105,810    31,519,529     1,413,720   5 Extended
/dev/sdb5          30,105,873    31,519,529     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5e7a983c-6f9c-405f-8cef-d8d58fa04b76" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="8a7a4042-9fec-44b4-8980-ec636f66d2c7" TYPE="ext3" 
/dev/sdb5: UUID="5ccd5362-cdff-4769-abfa-b8c397012f01" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)


=============================== sda1/etc/fstab: ===============================

aufs / aufs defaults 0 0 # AutoUpdate
devpts /dev/pts devpts gid=5,mode=620 0 0 # AutoUpdate
proc /proc proc defaults 0 0 # AutoUpdate
sysfs /sys sysfs defaults 0 0 # AutoUpdate
/dev/hdc1 /mnt/hdc1 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/hdd1 /mnt/hdd1 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/hdd5 /mnt/hdd5 swap auto,defaults 0 0 # AutoUpdate
/dev/sda1 /mnt/sda1 vfat auto,noatime,users,suid,dev,exec,quiet,umask=0,check=s,shortname=mixed 0 0 # AutoUpdate
/dev/fd0 /mnt/floppy vfat noauto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
tmpfs /tmp tmpfs defaults,noatime,mode=0777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=0777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0777 0 0

============================= sda1/etc/lilo.conf: =============================

#Backtrack

lba32
boot = /dev/hdc
prompt
timeout = 60
change-rules
reset
vga = 773
image = /boot/vmlinuz
root = /dev/hdc1
label = Back|track3


#ubuntu
other = /dev/hdd2
label = ubuntu
table = /dev/hdd
=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/vmlinuz

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
# kopt=root=UUID=8a7a4042-9fec-44b4-8980-ec636f66d2c7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8a7a4042-9fec-44b4-8980-ec636f66d2c7

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
# defoptions=quiet splash clocksource=hpet

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

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc
uuid		8a7a4042-9fec-44b4-8980-ec636f66d2c7
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=8a7a4042-9fec-44b4-8980-ec636f66d2c7 ro quiet splash clocksource=hpet 
initrd		/boot/initrd.img-2.6.27-8-eeepc
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc (recovery mode)
uuid		8a7a4042-9fec-44b4-8980-ec636f66d2c7
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=8a7a4042-9fec-44b4-8980-ec636f66d2c7 ro  single
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		Ubuntu 8.10, memtest86+
uuid		8a7a4042-9fec-44b4-8980-ec636f66d2c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Back|track3 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdc1 vga = 773 
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8a7a4042-9fec-44b4-8980-ec636f66d2c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5ccd5362-cdff-4769-abfa-b8c397012f01 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/menu.lst
   3.2GB: boot/grub/stage2
   3.2GB: boot/initrd.img-2.6.27-8-eeepc
   3.2GB: boot/vmlinuz-2.6.27-8-eeepc
   3.2GB: initrd.img
   3.2GB: vmlinuz
```

thanks again :D

---

### Post by caljohnsmith on 2009-05-05
Have you tried setting your sda drive first in your BIOS boot order and confirmed that Backtrack boots OK? Because if it doesn't, then obviously the problem is with your Backtrack installation and not Grub. Please let me know what you come up with and we can work from there.

John

---

### Post by MrCracker on 2009-05-05
Yes my ubuntu ssd is set to boot first and it works.

To boot backtrack i have to go into the boot menu and select the other ssd, which boots lilo where i select backtrack and it comes up without a problem.

---

### Post by MrCracker on 2009-05-06
So I guess there's no hope for me?

---

### Post by caljohnsmith on 2009-05-06
It looks like you might have to use Grub to directly boot Backtrack's kernel file, but I don't know off-hand what the correct parameters to use in the menu.lst entry. Before trying that, how about trying the following entries to boot Backtrack:
```
title Backtrack 3 #1
rootnoverify (hd1)
map        (hd0) (hd1)
chainloader +1

title Backtrack 3 #2
rootnoverify (hd1)
map        (hd1) (hd0)
chainloader +1

title Backtrack 3 #3
rootnoverify (hd1)
chainloader +1
```
Let me know if any of those above three entries work, and if not, please post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
ls -lR /mnt/boot
```
And we can work from there.

John

---

### Post by MrCracker on 2009-05-07
Hey!

So the first and third don't work but when I hit the second option, i get the following:

Starting up...
lilo:
error: duplicated volume id

and then after a couple seconds it boots up lilo, i select backtrack and backtrack boots up 

So I guess it works :D

Thanks !

---

### Post by caljohnsmith on 2009-05-07
That's an interesting result I wouldn't expect, but I guess as long as you can now boot Backtrack from Grub, you might as well stick with what works at this point. :)

Cheers,
John

---

