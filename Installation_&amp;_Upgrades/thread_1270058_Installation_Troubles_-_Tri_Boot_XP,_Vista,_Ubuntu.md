---
title: "Installation Troubles - Tri Boot: XP, Vista, Ubuntu"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by onehit on 2009-09-19
After installing Ubuntu on my WinXP+Win Vista system I can no longer boot into any of the windows partitions

I have created GRUB entries for each of the different partitions on my machine and nothing will boot but Ubuntu :( 

Does anyone have experience with this?

---

### Post by onehit on 2009-09-19
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
# kopt=root=UUID=adab72a6-b75c-4ae8-98fc-96fbf331e787 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=adab72a6-b75c-4ae8-98fc-96fbf331e787

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
uuid        adab72a6-b75c-4ae8-98fc-96fbf331e787
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=adab72a6-b75c-4ae8-98fc-96fbf331e787 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        adab72a6-b75c-4ae8-98fc-96fbf331e787
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=adab72a6-b75c-4ae8-98fc-96fbf331e787 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        adab72a6-b75c-4ae8-98fc-96fbf331e787
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=adab72a6-b75c-4ae8-98fc-96fbf331e787 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        adab72a6-b75c-4ae8-98fc-96fbf331e787
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=adab72a6-b75c-4ae8-98fc-96fbf331e787 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        adab72a6-b75c-4ae8-98fc-96fbf331e787
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Windows Vista (loader)
rootnoverify    (hd0,3)
savedefault
makeactive
chainloader    +1

title        Windows 1
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

title        Windows 2
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

title        Windows 3
rootnoverify    (hd0,3)
savedefault
makeactive
chainloader    +1

---

### Post by bumanie on 2009-09-19
You need to add the two windows bootloaders together. I have a triple boot with vista installed first, xp second and finally ubuntu. I probably will be going out soon, but can you post the output of > sudo fdisk -l and > sudo blkid. In a nutshell what I did was have vista installed first, then installed xp and recovered vista's bootloader with a repair cd. Then used [easybcd bootloader]("http://neosmart.net/dl.php?id=1") to add xp's boot files to vista's boot files - vista then gives the choice of booting into vista or xp. After that, I installed ubuntu as per the normal dual boot scenario and grub gives the choice of ubuntu and vista. If you choose vista, vista's bootloader will give the choice of vista or xp. If you don't have a vista repair cd, go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Of course, choose ubuntu and it will boot.

---

### Post by onehit on 2009-09-19
> **bumanie said:**
> You need to add the two windows bootloaders together. I have a triple boot with vista installed first, xp second and finally ubuntu. I probably will be going out soon, but can you post the output of  and . In a nutshell what I did was have vista installed first, then installed xp and recovered vista's bootloader with a repair cd. Then used [easybcd bootloader]("http://neosmart.net/dl.php?id=1") to add xp's boot files to vista's boot files - vista then gives the choice of booting into vista or xp. After that, I installed ubuntu as per the normal dual boot scenario and grub gives the choice of ubuntu and vista. If you choose vista, vista's bootloader will give the choice of vista or xp. If you don't have a vista repair cd, go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Of course, choose ubuntu and it will boot.

That sounds exactly like what I did.

I had Vista first then I installed XP then I used EasyBCD to allow both windows partitions to boot.

Before I installed Ubuntu I moved around the windows partitions with GParted though, not sure if thats what ****** up the bootloaders or not?

---

### Post by bumanie on 2009-09-19
Moving partitions certainly would confuse windows, the BCD (Boot Configuration Data) of vista (which I think is the rough of equivalent of xp's boot.ini file) has probably got the wrong partitions recorded in it. From ubuntu you should be able to go to the BCD of vista and open it with a text editor and check what the partitions are recorded as being. I have done this with boot.ini in xp and edited the file, but have not tried with vista, so can't help too much there. The other thing is to move the partitions back to where they were, which of course has the inherent risk of data loss/corruption - hopefully vista's BCD would then realign with the partition numbers it has recorded, but with moving things around so much, there would be no guarantees. You could reinstall and not move the partitions around. Not sure which would be easiest. 

Possibly editing vista's BCD would be easiest if it works, but as I have not tried it, so I am not 100% sure, I am going on past experience with doing the same to boot.ini. Suggest you do a bit of reading about vista's bootloader and how it allocates partitions. It is a good learning experience of what not to do and (hopefully) how to fix it.  Good luck.

PS: It is probably worth your while going [here]("http://members.iinet.net.au/~herman546/p15.html") and reading the section on vista issues with partitioning.

---

