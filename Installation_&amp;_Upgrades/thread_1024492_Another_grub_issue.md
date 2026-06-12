---
title: "Another grub issue"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by toontastic on 2008-12-29
Hi guys, I gave in trying to get football manager 2009 to run on Ubuntu for now as I just want to play it so I decided to finally reinstall Windows XP :(

Anyway I stole some 15gb off my /home partition and converted this into ntfs. I then installed my Windows XP SP3 CD on to this. Worked like a charm and I was able to boot straight into Windows.

I then went into the live CD ran 

```
- root (hd0,0)
- setup (hd0)
- quit
- exit
```

And this got me back into Ubuntu, so the next step was to get the grub to work with Windows. This is where I got confused.

I added 

```
title Windows XP
root (hd0,1)
makeactive
chainloader +1 
``` 

To the end of my menu.lst file but I now get an error instead of Windows trying to boot up.

Heres my info:

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
# kopt=root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,4)
makeactive
chainloader +1

```

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2   *        1217        1338      979965   82  Linux swap / Solaris
/dev/sda3            1339       28483   218042212+  83  Linux
/dev/sda4           28484       30401    15406335    7  HPFS/NTFS

```

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 457579395.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19535039     9767488+  83  Linux
/dev/sda2   *    19535040    21494969      979965   82  Linux swap / Solaris
/dev/sda3        21494970   457579394   218042212+  83  Linux
/dev/sda4       457579395   488392064    15406335    7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e" TYPE="ext3" 
/dev/sda2: UUID="a9abe04a-5bae-4a24-a468-7268d78d0187" TYPE="swap" 
/dev/sda3: UUID="dcd690a5-1f22-427c-80a3-51f5dd702887" TYPE="ext3" 
/dev/sda4: UUID="7EAC2DA7AC2D5B43" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/toontastic/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=toontastic)

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
# kopt=root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,4)
makeactive
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cfd92276-a5f7-4d9d-a3eb-1f77b1e5eb6e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=dcd690a5-1f22-427c-80a3-51f5dd702887 /home           ext3    relatime        0       2
# /dev/sda2
UUID=a9abe04a-5bae-4a24-a468-7268d78d0187 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 41572
drwxr-xr-x  3 root root    4096 2008-12-17 18:14 .
drwxr-xr-x 21 root root    4096 2008-12-29 07:53 ..
-rw-r--r--  1 root root  422838 2008-10-22 04:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   80062 2008-10-22 04:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-28 22:14 grub
-rw-r--r--  1 root root 7487866 2008-11-08 08:12 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7487759 2008-10-30 15:51 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8107951 2008-11-15 10:21 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8127865 2008-12-17 18:14 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-10-22 04:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920760 2008-10-22 04:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2008-12-28 22:14 .
drwxr-xr-x 3 root root   4096 2008-12-17 18:14 ..
-rw-r--r-- 1 root root    197 2008-10-04 15:17 default
-rw-r--r-- 1 root root     15 2008-10-04 15:17 device.map
-rw-r--r-- 1 root root   8056 2008-10-04 15:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-04 15:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-04 15:17 installed-version
-rw-r--r-- 1 root root   8608 2008-10-04 15:17 jfs_stage1_5
-rw-r--r-- 1 root root   5107 2008-12-28 22:14 menu.lst
-rw-r--r-- 1 root root   5107 2008-12-28 21:48 menu.lst~
-rw-r--r-- 1 root root   7324 2008-10-04 15:17 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-04 15:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-04 15:17 stage1
-rw-r--r-- 1 root root 108356 2008-10-04 15:17 stage2
-rw-r--r-- 1 root root   9276 2008-10-04 15:17 xfs_stage1_5

================================ sda4/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== StdErr Messages: ===============================

No errors were reported.
```

Hope this helps someone to help me.

Thanks in advance!

---

### Post by toontastic on 2008-12-29
Sorry I had changed in my grub to 

title Windows XP
root (hd0,4)
makeactive
chainloader +1

cause when it didn't work I was trying to work out why so changed it to hd0,4 because it sits on sda4. That was my logic anyway :)

---

### Post by toontastic on 2008-12-29
Finally, honest :) When I tried to boot Windows when grub was set to hd0,1 I get the error 

Invalid or unsupported executable format

---

### Post by Herman on 2008-12-29
```
title Windows XP
root (hd0,4)
makeactive
chainloader +1

```Linux and most humans start counting things from one most of the time, but a lot of things to do with computers start counting from the number zero. GRUB numbering begins with zero.
So /dev/sda4 in Linux numbering is equivalent to (hd0,3) in GRUB's numbering scheme, so you need,
```
title Windows XP
 root (hd0,3)
 makeactive
 chainloader +1
```That should work for you, (I hope),
Regards, Herman :)

---

### Post by toontastic on 2008-12-29
Must have been the only number I didn't try lol. Thank you very much!

---

