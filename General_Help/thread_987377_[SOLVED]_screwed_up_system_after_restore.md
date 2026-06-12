---
title: "[SOLVED] screwed up system after restore"
date: 2008-11-19
forum: General Help
---

### Post by hart02 on 2008-11-19
i upgraded from 8.04.1 to 8.10. before that i backuped my files using quickstart. with 8.04.1 my config files looked like this
menu.lst
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
default		10

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
# kopt=root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro

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
# defoptions=splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-21-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.04.1, kernel 2.6.24-21-virtual
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-virtual root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-21-virtual
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-virtual (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-virtual root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-virtual

title		Ubuntu 8.04.1, kernel 2.6.24-21-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-21-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-server

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, kernel 2.6.24-21-openvz
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-openvz root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-21-openvz
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-openvz (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-openvz root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-openvz

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-20-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-386

title		Ubuntu 8.04.1, kernel 2.6.24-20-virtual
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-virtual root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-20-virtual
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-virtual (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-virtual root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-virtual

title		Ubuntu 8.04.1, kernel 2.6.24-20-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-server root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-20-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-server root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-server

title		Ubuntu 8.04.1, kernel 2.6.24-20-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-rt root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-20-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-rt root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-rt

title		Ubuntu 8.04.1, kernel 2.6.24-20-openvz
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-openvz root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-20-openvz
quiet


title		Ubuntu 8.04.1, kernel 2.6.24-20-openvz (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-openvz root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-openvz

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sdc1
UUID=ee041c1f-34e0-432b-9718-000014ae2726  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sdc5
UUID=6254b2fb-08d9-4df4-b2bc-44dbc2fffdb6  none            swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd0                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdi1                                  /media/SanDisk  vfat         user,noauto,exec,utf8,rw  0  0  
```

mtab
```
/dev/sdc1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/scd1 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=brian 0 0
gvfs-fuse-daemon /home/brian/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=brian 0 0
/dev/sda1 /media/sda1 ext3 rw 0 0
/dev/sdd1 /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```

device.map
```
(hd0)	/dev/sdc
(hd1)	/dev/sdb
(hd2)	/dev/sda
(hd3)	/dev/sdd
```

with a fresh 8.10 they looked liked this

menu.lst
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
# kopt=root=UUID=4604ddf3-47b3-496b-82ee-08eaabe8ae51 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4604ddf3-47b3-496b-82ee-08eaabe8ae51

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4604ddf3-47b3-496b-82ee-08eaabe8ae51
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4604ddf3-47b3-496b-82ee-08eaabe8ae51 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4604ddf3-47b3-496b-82ee-08eaabe8ae51
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4604ddf3-47b3-496b-82ee-08eaabe8ae51 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4604ddf3-47b3-496b-82ee-08eaabe8ae51
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=4604ddf3-47b3-496b-82ee-08eaabe8ae51 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=b743f534-5ca3-4284-b6ab-1390876820b8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

mtab
```
/dev/sdd1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/brian/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=brian 0 0
/dev/scd0 /media/CDROM iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0
/dev/sdb1 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdc1 /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdi1 /media/disk-2 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda1 /media/disk-3 ext3 rw,nosuid,nodev,uhelper=hal 0 0
```

devices.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

/dev/sdd is where my os is 
reinstalled a few time to build 1 good remastersys iso (first installs were UUE Gamers which were to big)
after that i restored the files i had from 8.04.1 even the config files which is regrettable.

after some trouleshootings attempts i have this 

menu.lst
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
default		10

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
# root		(hd3,0)
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
# kopt=root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd3,0)
# groot=(hd3,0)

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
# defoptions=splash acpi=off noapic

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
# savedefault=true

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd3,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro all_generic_ide  acpi=off noapic 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault  
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-386
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-21-386
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-386 (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.10, kernel 2.6.24-21-virtual
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-virtual root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-21-virtual
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-virtual (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-virtual root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-virtual

title		Ubuntu 8.10, kernel 2.6.24-21-server
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-21-server
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-server (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-server

title		Ubuntu 8.10, kernel 2.6.24-21-rt
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-rt (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.10, kernel 2.6.24-21-openvz
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-openvz root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-21-openvz
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-openvz (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-openvz root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-openvz

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.24-20-386
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-20-386
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-386 (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-386

title		Ubuntu 8.10, kernel 2.6.24-20-virtual
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-virtual root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-20-virtual
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-virtual (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-virtual root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-virtual

title		Ubuntu 8.10, kernel 2.6.24-20-server
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-server root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-20-server
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-server (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-server root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-server

title		Ubuntu 8.10, kernel 2.6.24-20-rt
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-rt root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-20-rt
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-rt (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-rt root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-rt

title		Ubuntu 8.10, kernel 2.6.24-20-openvz
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-openvz root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-20-openvz
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-openvz (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-openvz root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-openvz

title		Ubuntu 8.10, kernel 2.6.24-20-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 ro  all_generic_ide  acpi=off noapic
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-20-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=9f1fa354-27bb-4dcc-86de-b563feaa0a92 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=b743f534-5ca3-4284-b6ab-1390876820b8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

mtab
```
/dev/sdd1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/scd0 /media/CDROM iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0
/dev/sdb1 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdc1 /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdi1 /media/disk-2 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda1 /media/disk-3 ext3 rw,nosuid,nodev,uhelper=hal 0 0
```

devices.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

and /dev/disk/by-uuid/ has these

```
root@ubuntu:/# ls /dev/disk/by-uuid/
48E5-7F09			      b743f534-5ca3-4284-b6ab-1390876820b8
6b854a99-0adb-4dc5-beba-1301a54198f9  dd38e47c-5d07-44d0-9296-31669d00c63a
9f1fa354-27bb-4dcc-86de-b563feaa0a92

```

booting normally takes me to busybox says stuff i cant read fast enough:confused:

if anyone can help me with this so i do not have to reinstall thus having to consume more time with configuring that would be appreciated.:) i have important stuff to do.

---

### Post by drs305 on 2008-11-19
Unfortunately, the posted results of the command you used to obtain the uuid's doesn't give us the full picture. Since your new-original fstab and new-modified fstab uuid's are not the same, we need to verify the existing partition structure/uuid's.

Please post the results of:
```
sudo blkid
```

---

### Post by hart02 on 2008-11-19
this is what i got

```
root@ubuntu:/# sudo blkid
/dev/sda1: UUID="6b854a99-0adb-4dc5-beba-1301a54198f9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="9f1fa354-27bb-4dcc-86de-b563feaa0a92" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="48E5-7F09" TYPE="vfat" 
/dev/sdd1: UUID="dd38e47c-5d07-44d0-9296-31669d00c63a" TYPE="ext3" 
/dev/sdd5: TYPE="swap" UUID="b743f534-5ca3-4284-b6ab-1390876820b8" 
/dev/loop0: TYPE="squashfs"
```

---

### Post by drs305 on 2008-11-19
Make copies of your current fstab and menu.lst files.

Make the changes to your fstab and menu.lst and we can see if it boots. The following assumes that /dev/sdd1 is your linux partition. If it is /dev/sda1 replace the UUID with the /dev/sda1 UUID:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sdd1
UUID=dd38e47c-5d07-44d0-9296-31669d00c63a  /   ext3     relatime,errors=remount-ro  0  1  
# /dev/sdd5
UUID=b743f534-5ca3-4284-b6ab-1390876820b8  none  swap  sw 0 0 
  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd0                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdi1                                  /media/SanDisk  vfat         user,noauto,exec,utf8,rw  0  0

```

If you haven't changed the last menu.lst you posted, and sdd1 is your ubuntu partition, change the first entry in your menu.lst to:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd3,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=dd38e47c-5d07-44d0-9296-31669d00c63a  ro all_generic_ide  acpi=off noapic 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault  
quiet

```

---

### Post by hart02 on 2008-11-19
i will try that and let you know.
should i do it for all of them

---

### Post by drs305 on 2008-11-19
> **hart02 said:**
> i will try that and let you know.
should i do it for all of them

Personally, I would leave all the other entries alone for now. As soon as you get it booting properly I can make some suggestions as to those entries as well. 

See if you can make the change to the first selection in the menu.lst (and fstab) and get it to boot.

---

### Post by hart02 on 2008-11-19
well good news and bad. goods news is that busybox did not appear. instead  
it had stopped saying that the kernel panicked and the keyboard stopped responding. i rebooted to livecd to post this

---

### Post by Bluebell392 on 2008-11-19
What does the kernel say right before the kernel panic message?

---

### Post by drs305 on 2008-11-19
I think I know - I may have pasted the wrong uuid for the first choice, leaving it what was originally in there. 

The correct UUID for the first choice in menu.lst should read the following if the system is on sdd1:
> 
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd3,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=dd38e47c-5d07-44d0-9296-31669d00c63a  ro all_generic_ide  acpi=off noapic 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault  
quiet


If you can get back to the boot menu, hit ESC while it is booting, then cursor down to the first choice in the grub menu, hit E (for Edit), cursor down to the line with the UUID, hit E again, and type in the correct UUID. Then hit Enter and ESC until you are back to the main menu. Boot. We can edit grub once you have successfully booted, as the change is not permanent.

---

### Post by hart02 on 2008-11-19
unless i can find the log that says what the machines is doing to before loading the os I will have to go back and check it during boot for i did not see all of it.wheres is that file anyway?

---

### Post by Bluebell392 on 2008-11-19
The kernel log file is under /var/log/kern.log, but if you can't find the boot messages, it might be under kern.log.0.

---

### Post by hart02 on 2008-11-19
I now have photos of what happens. you might need to zoom in.
here is a summary :
```
Begin mounting root file system:
init line 190 :syntax error 0xdd38e47c-5d07-44d0-9296-3166900c63a
[2.771629] Kernel panic - not syncing: attempted to kill init
```

---

### Post by Bluebell392 on 2008-11-19
This explains the kernel panic: [Explained kernel panic not syncing attempted to kill init- LinuxQuestions.org]("http://http://www.linuxquestions.org/questions/linux-software-2/explained-kernel-panic-not-syncing-attempted-to-kill-init-353920/") It looks like a UUID was either incorrect or mistyped. Find the correct UUID, and use that instead.

---

### Post by hart02 on 2008-11-19
something tells me that i must do a reinstall to fix this.Great. I will have fun doing that again for the 5th or 6th time. and after all i have done on my machine. all the recent work that has not been backed up will be gone if i do that. well i have had worse like not having any data at all. if there is a few things i have learned it is that 1.when upgrading DO NOT RESTORE the old config files that quickstart backup made on previous installs if you want to avoid a troublesome headache.2.use the previous config tarball files as reference 3.keep good backups with programs like quickstart.4 prepare for the worst possible outcome with a good disaster recovery plan. if i cant find an answer here on the internet then a reinstall it is unless i am told otherwise.

---

### Post by Bluebell392 on 2008-11-19
> **drs305 said:**
> I think I know - I may have pasted the wrong uuid for the first choice, leaving it what was originally in there. 

The correct UUID for the first choice in menu.lst should read the following if the system is on sdd1:

title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd3,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=dd38e47c-5d07-44d0-9296-31669d00c63a ro all_generic_ide acpi=off noapic
initrd /boot/initrd.img-2.6.27-7-generic
savedefault
quiet 

If you can get back to the boot menu, hit ESC while it is booting, then cursor down to the first choice in the grub menu, hit E (for Edit), cursor down to the line with the UUID, hit E again, and type in the correct UUID. Then hit Enter and ESC until you are back to the main menu. Boot. We can edit grub once you have successfully booted, as the change is not permanent.

This was on the previous page, and I think it might help.

---

### Post by hart02 on 2008-11-19
here are the pictures that i said i would post.On several occasions i've tried changing (hd3,0) to (hd0,0) to no avail.

---

### Post by drs305 on 2008-11-19
The issue may be which partition has the OS on it. You also have sda1 and sdb1, which are also ext3 drives. As I mentioned, the templates are for sdd1. Are you sure the system is not on either sda1 or sdb1? 

If you don't know how to check, from the livecd desktop, open a terminal.
Make a temporary directory:
```
sudo mkdir /mnt/temp

```

Mount a partition:
```

sudo mount /dev/sda1 /mnt/temp 

```

Check the contents to see if an OS kernel is present:
```

ls /mnt/temp/boot

```

If not:
```
sudo umount /dev/sda1
```

Repeat for /dev/sdb1.

If not, repeat to confirm the OS is on sdd1

---

### Post by hart02 on 2008-11-19
here is some command output
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ ls /mnt/temp/boot
ls: cannot access /mnt/temp/boot: No such file or directory
ubuntu@ubuntu:~$ sudo umount /dev/sda1 
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/temp
ubuntu@ubuntu:~$ ls /mnt/temp/boot
ls: cannot access /mnt/temp/boot: No such file or directory
ubuntu@ubuntu:~$ ls /mnt/boot
abi-2.6.24-20-386                 initrd.img-2.6.24-21-virtual
abi-2.6.24-20-generic             initrd.img-2.6.25-2-386
abi-2.6.24-20-server              initrd.img-2.6.27-6.slh.5-sidux-686
abi-2.6.24-20-virtual             initrd.img-2.6.27-7-generic
abi-2.6.24-21-386                 initrd.img-2.6.27-8-generic
abi-2.6.24-21-generic             memtest86+.bin
abi-2.6.24-21-server              sarge.bmp
abi-2.6.24-21-virtual             sbm.img
abi-2.6.25-2-386                  sid.bmp
abi-2.6.27-7-generic              System.map-2.6.24-20-386
abi-2.6.27-8-generic              System.map-2.6.24-20-generic
abi-2.6.27-8-server               System.map-2.6.24-20-openvz
coffee.bmp                        System.map-2.6.24-20-rt
config-2.6.24-20-386              System.map-2.6.24-20-server
config-2.6.24-20-generic          System.map-2.6.24-20-virtual
config-2.6.24-20-openvz           System.map-2.6.24-21-386
config-2.6.24-20-rt               System.map-2.6.24-21-generic
config-2.6.24-20-server           System.map-2.6.24-21-openvz
config-2.6.24-20-virtual          System.map-2.6.24-21-rt
config-2.6.24-21-386              System.map-2.6.24-21-server
config-2.6.24-21-generic          System.map-2.6.24-21-virtual
config-2.6.24-21-openvz           System.map-2.6.25-2-386
config-2.6.24-21-rt               System.map-2.6.27-6.slh.5-sidux-686
config-2.6.24-21-server           System.map-2.6.27-7-generic
config-2.6.24-21-virtual          System.map-2.6.27-8-generic
config-2.6.25-2-386               System.map-2.6.27-8-server
config-2.6.27-6.slh.5-sidux-686   vmcoreinfo-2.6.27-7-generic
config-2.6.27-7-generic           vmcoreinfo-2.6.27-8-generic
config-2.6.27-8-generic           vmcoreinfo-2.6.27-8-server
config-2.6.27-8-server            vmlinuz-2.6.24-20-386
debian.bmp                        vmlinuz-2.6.24-20-generic
debianlilo.bmp                    vmlinuz-2.6.24-20-openvz
grub                              vmlinuz-2.6.24-20-rt
initrd.img-2.6.24-20-386          vmlinuz-2.6.24-20-server
initrd.img-2.6.24-20-generic      vmlinuz-2.6.24-20-virtual
initrd.img-2.6.24-20-openvz       vmlinuz-2.6.24-21-386
initrd.img-2.6.24-20-openvz.bak   vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-20-rt           vmlinuz-2.6.24-21-openvz
initrd.img-2.6.24-20-server       vmlinuz-2.6.24-21-rt
initrd.img-2.6.24-20-virtual      vmlinuz-2.6.24-21-server
initrd.img-2.6.24-21-386          vmlinuz-2.6.24-21-virtual
initrd.img-2.6.24-21-386.bak      vmlinuz-2.6.25-2-386
initrd.img-2.6.24-21-generic      vmlinuz-2.6.27-6.slh.5-sidux-686
initrd.img-2.6.24-21-generic.bak  vmlinuz-2.6.27-7-generic
initrd.img-2.6.24-21-openvz       vmlinuz-2.6.27-8-generic
initrd.img-2.6.24-21-rt           vmlinuz-2.6.27-8-server
initrd.img-2.6.24-21-server
ubuntu@ubuntu:~$ sudo umount /dev/sdb1 /mnt/temp
umount: /dev/sdb1: not mounted
ubuntu@ubuntu:~$ 


```

It's on sdd alright. should it be on sda? how do i make it the first drive to boot up?

---

### Post by hart02 on 2008-11-20
I got it to boot finally and it was so obvious too.
it was these lines
```

## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ee041c1f-34e0-432b-9718-000014ae2726 ro

```

I just edited them to 

```

## e.g. kopt=root=/dev/sdd1 ro
##      kopt_2_6_8=root=/dev/sdd1 ro
##      kopt_2_6_8_2_686=root=/dev/sdd2 ro
# kopt=root=UUID=dd38e47c-5d07-44d0-9296-31669d00c63a ro

```

now it boots:D

---

