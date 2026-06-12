---
title: "Dual booting Fedora 11 &amp; Jaunty"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by boarder428 on 2009-10-20
Still having problems learning to read/edit the boot menu.  My goal here was to install Fedora 11 and Jaunty side by side.  I first started with Fedora installed and tried to install Jaunty.  The Ubuntu Installer did not detect any other Os's on the disk so I let it do a clean install figuring I would re-install Fedora after the Ubuntu install.  After installing Fedora I can only boot to Fedora and it's boot manager does not show Ubuntu.  I know it's there but cannot seem to figure out how to link the 2 to one boot menu?  ```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 205118529 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #3 for /grub/grub.conf.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda4: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0754010c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   204,800,062   204,800,000  83 Linux
/dev/sda2         482,383,755   488,392,064     6,008,310   5 Extended
/dev/sda5         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris
/dev/sda3    *    204,800,063   205,209,662       409,600  83 Linux
/dev/sda4         205,209,663   482,383,754   277,174,092  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2083 MB, 2083520512 bytes
64 heads, 32 sectors/track, 1987 cylinders, total 4069376 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2d7b3e8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,069,374     4,069,343   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="22495310-62a3-4506-b0e1-409dc0bb6297" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="ac524224-8f92-44ff-bfff-d6cc4bb1de5f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="9ZjgeH-q2Ch-H9Vm-HSe1-Yav0-6UvO-FsmhXR" TYPE="lvm2pv" 
/dev/sda5: TYPE="swap" UUID="1c742787-7a0a-4e4c-9a87-41251fad8181" 
/dev/sdb1: SEC_TYPE="msdos" UUID="3653-0D32" TYPE="vfat" 

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
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=22495310-62a3-4506-b0e1-409dc0bb6297 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=22495310-62a3-4506-b0e1-409dc0bb6297

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		22495310-62a3-4506-b0e1-409dc0bb6297
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=22495310-62a3-4506-b0e1-409dc0bb6297 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		22495310-62a3-4506-b0e1-409dc0bb6297
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=22495310-62a3-4506-b0e1-409dc0bb6297 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		22495310-62a3-4506-b0e1-409dc0bb6297
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=22495310-62a3-4506-b0e1-409dc0bb6297 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		22495310-62a3-4506-b0e1-409dc0bb6297
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=22495310-62a3-4506-b0e1-409dc0bb6297 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		22495310-62a3-4506-b0e1-409dc0bb6297
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=22495310-62a3-4506-b0e1-409dc0bb6297 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c742787-7a0a-4e4c-9a87-41251fad8181 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  50.3GB: boot/grub/menu.lst
  50.3GB: boot/grub/stage2
  50.4GB: boot/initrd.img-2.6.28-11-generic
  50.3GB: boot/initrd.img-2.6.28-15-generic
  50.4GB: boot/vmlinuz-2.6.28-11-generic
  50.3GB: boot/vmlinuz-2.6.28-15-generic
  50.3GB: initrd.img
  50.4GB: initrd.img.old
  50.3GB: vmlinuz
  50.4GB: vmlinuz.old

============================= sda3/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=1
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.30.8-64.fc11.i586)
	root (hd0,2)
	kernel /vmlinuz-2.6.30.8-64.fc11.i586 ro root=/dev/mapper/VolGroup-lv_root rhgb quiet
	initrd /initrd-2.6.30.8-64.fc11.i586.img
title Fedora (2.6.29.4-167.fc11.i586)
	root (hd0,2)
	kernel /vmlinuz-2.6.29.4-167.fc11.i586 ro root=/dev/mapper/VolGroup-lv_root rhgb quiet
	initrd /initrd-2.6.29.4-167.fc11.i586.img

=================== sda3: Location of files loaded by Grub: ===================


 105.0GB: grub/grub.conf
 105.0GB: grub/menu.lst
 105.0GB: grub/stage2
 104.8GB: initrd-2.6.29.4-167.fc11.i586.img
 104.8GB: initrd-2.6.30.8-64.fc11.i586.img
 104.8GB: vmlinuz-2.6.29.4-167.fc11.i586
 104.8GB: vmlinuz-2.6.30.8-64.fc11.i586
```

---

### Post by Soul-Sing on 2009-10-20
maybe this thread is helpful? : [http://ubuntuforums.org/showthread.php?t=1225972&highlight=Dual+booting+Fedora+Jaunty](http://ubuntuforums.org/showthread.php?t=1225972&highlight=Dual+booting+Fedora+Jaunty)

---

### Post by presence1960 on 2009-10-20
what you want to do is put Jaunty's GRUB on MBR of sda and then chainload Fedora from jaunty's GRUB. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Boot into Ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

Scroll down to:
**### END DEBIAN AUTOMAGIC KERNELS LIST**

skip one line and add this entry:

```
title           Fedora
rootnoverify    (hd0,2)
chainloader     +1
```

Click Save on toolbar & close file. Reboot and use the Fedora entry you just added when the GRUB menu comes up to boot into Fedora. If successful you can remove any other Fedora entries in menu.lst. All you will need is the chainloaded entry you just added.

---

### Post by boarder428 on 2009-10-22
> **leoquant said:**
> maybe this thread is helpful? : [http://ubuntuforums.org/showthread.php?t=1225972&highlight=Dual+booting+Fedora+Jaunty](http://ubuntuforums.org/showthread.php?t=1225972&highlight=Dual+booting+Fedora+Jaunty)

Thanks for this link!  Definetly gives me some things to consider, looks like I should have keep it the way I had it previously with Fedora installed first.  Got confused when Ubuntu did'nt see Fedora installed.  If I would have chosen a manual install I could have directed Ubuntu's install!

> **presence1960 said:**
> what you want to do is put Jaunty's GRUB on MBR of sda and then chainload Fedora from jaunty's GRUB. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

For the most part I think I am starting to see how grub works.  For the most part this worked except I got the error when choosing Fedora from the boot menu, "Error 13: Invalid or unsupported executable format" when using the following in the boot menu.
```
title           Fedora
rootnoverify    (hd0,2)
chainloader     +1
```

So I cheated and installed fedora on another computer and robbed the following entry from it's boot list and managed to get both os's to boot!
```
title Fedora (2.6.29.4-167.fc11.i586)
	root (hd0,2)
	kernel /vmlinuz-2.6.29.4-167.fc11.i586 ro root=/dev/mapper/VolGroup-lv_root rhgb quiet
	initrd /initrd-2.6.29.4-167.fc11.i586.img
```

So thanks to all I seem to have a fix for the problem!

---

### Post by running_rabbit07 on 2009-10-22
Check out my thread where I fought this battle. [My thread.]("http://ubuntuforums.org/showthread.php?t=1234034") The finishing touch was somewhere near post 19.

---

