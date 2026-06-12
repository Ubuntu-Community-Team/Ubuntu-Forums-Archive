---
title: "Dual boot ubuntu &amp; backtrack 2 - eeepc"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by panher on 2009-10-13
Hi All,

 I seem to have run into some problem with my "attempted" dual boot install of ubuntu 9.04 and BT2 and kindly seek your assistance.

Being a newbie, I'll try and break down the installation strategy which I used and which may well be, the root of my problems.

1. Booted using a live ubuntu  cd (on usb) and used the partition editor to create a partition of about 15 GIG and formatted it using ext3. I left the rest of my 80GIG drive as free space.
2.I the Booted using a live BT2  cd (on usb) and installed BT2 (real) using the defaults. I had no problems to this stage and was able to boot into BT with no issues.
3. Booted using a live ubuntu  cd (on usb) and installed ubuntu manually. I believe I created a swap area of 1024MB which I understand should match the amount ram on the machine with the normal procedure of using the rest rest of the drive as /. Again, I had no problems booting in Ubuntu BUT do not recollect trying to boot into BT at this stage. I don't think I did though.
4. As has become a habit of mine, I quicky edited the edit grub for primarily cosmetic reasons and to disable(comment out) the the timeout. Grub code is shown below.
5. I can now boot into Jaunty with no problems but when I try and boot into BT2, I get the following error 
```
Please append a correct “root =” boot option
Kernel panic – not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
<4>atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying to access
hardware directly.

```5. DISK INFO
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+  83  Linux
/dev/sda2        30716280   156296384    62790052+   5  Extended
/dev/sda5        30716343    32708339      995998+  82  Linux swap / Solaris
/dev/sda6        32708403   156296384    61793991   83  Linux

```GRUB
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Pretty colours
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
# kopt=root=UUID=d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b

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

title        Jaunty 
uuid        d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        d9a0b942-a4bf-4524-a17d-2aa2ea11ef2b
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Backtrack 2
root        (hd0,0)
kernel        /boot/vmlinuz root=current ro vga = 0x317 
initrd        /boot/splash.initrd
savedefault
boot

```Thanks for your time and expertise.
[FONT=Times][SIZE=3][FONT=Times]. 
 [/FONT][/SIZE][/FONT]

---

### Post by presence1960 on 2009-10-13
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

