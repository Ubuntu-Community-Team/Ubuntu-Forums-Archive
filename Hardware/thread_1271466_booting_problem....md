---
title: "booting problem..."
date: 2009-09-20
forum: Hardware
---

### Post by kiran pawar on 2009-09-20
I have windows vista and ubuntu 8.10 on my Dell laptop inspiron 1545.
Unfortunately ,I hav deleted my /boot/grub/menu.lst 
But recovered soon using upgrade grub command 
then i added entry for vista but it unable to load vista 
only starting up.... message is shown for an hour n nothing
 i can only boot ubuntu. Please tell the way to recover vista. I have my valuable doccuments on c drive of vista. Please help me
 I m hereby attaching my /boot/grub/menu.lst   



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
timeout        3

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
# kopt=root=UUID=50990500-0e75-42a9-9331-b7ef403fa764 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=50990500-0e75-42a9-9331-b7ef403fa764

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        50990500-0e75-42a9-9331-b7ef403fa764
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=50990500-0e75-42a9-9331-b7ef403fa764 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        50990500-0e75-42a9-9331-b7ef403fa764
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=50990500-0e75-42a9-9331-b7ef403fa764 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        50990500-0e75-42a9-9331-b7ef403fa764
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1  title         Longhorn
title           Windows Vista/Longhorn (loader)
root           (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by 73ckn797 on 2009-09-20
See if this link will resolve your problem(s).
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I have and it works.

---

### Post by kiran pawar on 2009-09-21
i have windows vista installed first and then ubuntu
there is no problem in grub recovery
i can see grub and all entries of os too.
but the problem is when press ENTER on Windows Vista/Longhorn (loader)
it shows black screen with starting up.... in leftmost corner
it remains as it is n nothing
if i changed entries of rootnoverify as (hd0,1) or other it shows " NO BTMGR found press Alt +Ctrl +Del" 
so i can get into ubuntu only....
can u suggest any way to get boot into vista because grub is unable to find it ?

---

