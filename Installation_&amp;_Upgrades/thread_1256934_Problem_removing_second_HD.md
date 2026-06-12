---
title: "Problem removing second HD"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by artisan on 2009-09-03
I am running Ubuntu 9.04 Jaunty Jackalope on my main HD and am trying to remove a second HD.

After removing/unplugging the second HD and I try to reboot into the main HD there is: Error 15: file not found

I have tried to change the MBR using super grub disk and the Ubuntu cd.

No joy.

The original HD will not boot.
I don't know much about MBR and I wish to keep the information on the original HD.

Any suggestions? Any help appreciated.

Thanks.

---

### Post by presence1960 on 2009-09-03
Let's get a better look at your setup. Boot the Ubuntu Live CD without the disk you want to remove. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by artisan on 2009-09-04
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /grub/stage2 and /grub/menu.lst.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1672f2fe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   612,992,204   612,992,142  83 Linux
/dev/sda2         612,992,205   625,137,344    12,145,140   5 Extended
/dev/sda5         612,992,268   625,137,344    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="bf6a217b-debb-4257-b7d9-c485a0cd48a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="2572b847-400a-4be0-99a5-530b36d82473" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf6a217b-debb-4257-b7d9-c485a0cd48a4

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
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bf6a217b-debb-4257-b7d9-c485a0cd48a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf6a217b-debb-4257-b7d9-c485a0cd48a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2572b847-400a-4be0-99a5-530b36d82473 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 241.2GB: boot/grub/menu.lst
 241.3GB: boot/grub/stage2
 241.2GB: boot/initrd.img-2.6.27-11-generic
 241.3GB: boot/initrd.img-2.6.28-11-generic
 241.2GB: boot/initrd.img-2.6.28-13-generic
 241.3GB: boot/initrd.img-2.6.28-14-generic
 241.3GB: boot/initrd.img-2.6.28-15-generic
 241.2GB: boot/vmlinuz-2.6.27-11-generic
 241.2GB: boot/vmlinuz-2.6.28-11-generic
 241.2GB: boot/vmlinuz-2.6.28-13-generic
 241.2GB: boot/vmlinuz-2.6.28-14-generic
 241.2GB: boot/vmlinuz-2.6.28-15-generic
 241.3GB: initrd.img
 241.3GB: initrd.img.old
 241.2GB: vmlinuz
 241.2GB: vmlinuz.old
```

Thanks

---

### Post by presence1960 on 2009-09-04
Your GRUB is pointing to disk #2 which is no longer in your machine.  So you need to restore GRUB. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,0)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 use setup (hd0)
```

Then reboot and choose Ubuntu 9.04.
You should clean up your GRUB menu if you are not putting that other disk back in. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```

scroll down and remove these entries:
```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d7ac887f-20d5-40de-b577-77411513f594 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

---

### Post by artisan on 2009-09-04
Thank you for that.

I will take a look and let you know.

once again thanks.

---

### Post by artisan on 2009-09-04
That worked. The original HD now boots.
:)
I have one question. When the computer is first booting, the screen is black, at the top right a message pops up saying that there is no HD detected.
It doesn't look like an issue because the HD boots. But, is there some way to clear this.

Thanks.

---

### Post by presence1960 on 2009-09-04
> **artisan said:**
> That worked. The original HD now boots.
:)
I have one question. When the computer is first booting, the screen is black, at the top right a message pops up saying that there is no HD detected.
It doesn't look like an issue because the HD boots. But, is there some way to clear this.

Thanks.

Don't know about that one. I would leave well enough alone. Enjoy Ubuntu!

---

### Post by artisan on 2009-09-04
> **presence1960 said:**
> Don't know about that one. I would leave well enough alone. Enjoy Ubuntu!
:)

Yes, no problem there.

Thank you for help.

---

