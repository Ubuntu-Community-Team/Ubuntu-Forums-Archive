---
title: "Unable to recover"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2009-05-19
[LIST]
[*]Setup : Dual boot Jaunty with Windows
[*]Jaunty's Grub complains "Error 15 : File not found"
[*]Windows's Grub option works
[/LIST]

I used the live CD to recover the grub, while those steps succeeded [ find /boot/grub/stage1 followed by root ( hdx,x ) setup( hdx ) ], the problem has not gone away.

I'm unable to get to Linux.

My suspicion for this problem from what I can recollect is the last time I used Jaunty, there were few old release of Linux that showed up under "obselete" in Synaptics. I removed all those that showed up. Not fully sure if this is what screwed up the Grub or even removed the necessary files.


[LIST]
[*]How to fix this ?
[*]How to check if the core file were deleted ?
[/LIST]
Thanks.

---

### Post by dstew on 2009-05-19
Perhaps you deleted a kernel that was the one the grub menu points to, and for some reason update-grub did not put in a menu item for the more recent one. Post to the forum the output of ```
cat /boot/grub/menu.lst
```and```
ls -l /boot
```

---

### Post by shankariyer on 2009-05-19
Here we go...

> 
ubuntu@ubuntu:/storage/boot/grub$ cat menu.lst
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
timeout        6

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=7e7e3923-9a8a-4cb5-9975-18f8030c25db ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7e7e3923-9a8a-4cb5-9975-18f8030c25db

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        7e7e3923-9a8a-4cb5-9975-18f8030c25db
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=7e7e3923-9a8a-4cb5-9975-18f8030c25db ro quiet splash
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        7e7e3923-9a8a-4cb5-9975-18f8030c25db
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=7e7e3923-9a8a-4cb5-9975-18f8030c25db ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        7e7e3923-9a8a-4cb5-9975-18f8030c25db
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7e7e3923-9a8a-4cb5-9975-18f8030c25db ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        7e7e3923-9a8a-4cb5-9975-18f8030c25db
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7e7e3923-9a8a-4cb5-9975-18f8030c25db ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        7e7e3923-9a8a-4cb5-9975-18f8030c25db
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
#map        (hd0) (hd1)
#map        (hd1) (hd0)


> 
ubuntu@ubuntu:/storage/boot$ ls -lhrt
total 14M
-rw-r--r-- 1 root root 126K 2009-03-27 20:12 memtest86+.bin
-rw-r--r-- 1 root root 3.4M 2009-04-17 03:34 vmlinuz-2.6.28-11-generic
-rw-r--r-- 1 root root 1.8M 2009-04-17 03:34 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root  89K 2009-04-17 03:34 config-2.6.28-11-generic
-rw-r--r-- 1 root root 514K 2009-04-17 03:34 abi-2.6.28-11-generic
-rw-r--r-- 1 root root 1.2K 2009-04-17 03:39 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 7.6M 2009-05-05 00:42 initrd.img-2.6.28-11-generic
drwxr-xr-x 2 root root 4.0K 2009-05-16 02:09 grub


---

### Post by shankariyer on 2009-05-19
Changing "2.6.27-9" to "2.6.28-11" did the trick. Thanks for the pointer dstew.

Can't figure out what Synaptic did and why it marked few of these are "obsolete".

---

### Post by shankariyer on 2009-05-19
[FONT=Verdana]This is what I did...
[/FONT]
[LIST]
[*][FONT=Verdana]Use Ubuntu Live CD
[/FONT]
[*][FONT=Verdana]Locate the drive where Linux is installed using "df -h" ( /dev/sdb10 in my case )[/FONT]
[*][FONT=Verdana]Create a temp directory to mount the Linux partition ( e.g. sudo mkdir /storage )
[/FONT]
[*][FONT=Verdana]Modify /etc/fstab for the newly created directory like the following example
/dev/sdb10 /storage ext3 defaults 0,0[/FONT]
[*][FONT=Verdana]Mount the drive, with the updated fstab information using "mount -a"[/FONT]
[*][FONT=Verdana]Edit the menu.lst under /storage/boot/grub/menu.lst[/FONT]
[*][FONT=Verdana]Reboot and access Linux ( for the updated version )
[/FONT]
[/LIST]

---

