---
title: "MBR Set up Help! - dual boot windows xp and ubuntu- xp wont boot up!"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by Kat_129 on 2009-08-23
Hi, 
I am having a bit of understanding how to reset the MBR(master Boot Record).
First of the all the problem started after i installed Ubuntu, with windows XP( dual boot was set up andi  choose 2 pick windows as my first choice) . 
The problem is that  windows won't boot up, they barely get past the GRUB stage 2. I Know the the NTFS partition is still there( checked it using GParted- pic attached ) and I just don't know which would be the best way of fixing it or how do it. :(

I don't know where to start, if i  can be guide through  the steps on what I should be doing. Also I am not sure where to look for help either. please guide! 
Thanks in advance! 
kat 

Here is the Summary output when i checked the partition by fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2e26367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7649       15810    65550781+  83  Linux
/dev/sda3           15811       16357     4393777+  82  Linux swap / Solaris
/dev/sda4           16358       19457    24900750    5  Extended
/dev/sda5           16358       19457    24900718+   b  W95 FAT32

Disk /dev/sdb: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xef5198c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7868     2014192    6  FAT16

---

### Post by stlsaint on 2009-08-23
so from what i get you are choosing to make xp the primary boot...in a dual booting system...but you dont want to choose what OS to boot...you just want to boot straight to XP?? well im not sure thats going to work with GRUB that particular way unless you use BUM or startup manager in ubuntu to set what to boot. not 100% percent sure on that so wait for others to input boot it sounds like that you may need to rewrite xp to the MBR!! that should be able to be done with recovery disc or xp disc.

---

### Post by ASchweitzer on 2009-08-23
What exactly does grub do when you boot? Does it give you a menu of operating systems to choose from (you may have to press esc to bring this up)? Is windows listed?

Can you post */boot/grub/menu.lst* please? This is the grub configuration file. Towards the bottom all the Ubuntu options are listed, and at the very bottom there should be a listing that would boot you into windows.

---

### Post by Kat_129 on 2009-08-23
When i try 2 boot into windows, the windows dont boot up. They get stuck at grub stage 2. I am certain that, while installing ubnutu i didnt touch the C: hence windowns shouldn't have been affected but for some reason they won't boot - so i think i need to step up my MBR again. is that right ? I just dont want to reinstall windows since there were installed by my school.  
Thanks in advance! 

here is the */boot/grub/menu.lst*. 

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
default        saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=55fc7d9b-e760-4b43-8d8c-521122a372a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=55fc7d9b-e760-4b43-8d8c-521122a372a4

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        55fc7d9b-e760-4b43-8d8c-521122a372a4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=55fc7d9b-e760-4b43-8d8c-521122a372a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        55fc7d9b-e760-4b43-8d8c-521122a372a4
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=55fc7d9b-e760-4b43-8d8c-521122a372a4 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        55fc7d9b-e760-4b43-8d8c-521122a372a4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=55fc7d9b-e760-4b43-8d8c-521122a372a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        55fc7d9b-e760-4b43-8d8c-521122a372a4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=55fc7d9b-e760-4b43-8d8c-521122a372a4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        55fc7d9b-e760-4b43-8d8c-521122a372a4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

---

### Post by nhanquy on 2009-08-23
> **Kat_129 said:**
> Hi, 
I am having a bit of understanding how to reset the MBR(master Boot Record).


The MBR is the first 512 bytes of the disk and it has been wiped out by GRUB if you installed Ubuntu after Windows. Maybe it has been corrupted.

Boot the liveCD and use GRUB to fix the MBR, I think you will be OK.


[B]$sudo grub
>root (hd0,1)
>setup (hd0)
>quit[/B]


reboot PC!

---

