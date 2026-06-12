---
title: "Need help with dual boot setup....please!!!"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by the-dude on 2009-11-04
I am new to Linux, and after a lot of work I have the system usable, but it's not completely correct.

 I have XP installed on two 320gb sata drive in RAID 1, and Ubuntu on a separate 320gb sata drive. The single HDD with Ubuntu is set as the first hard drive in BIOS, GRUB loads just fine and gives me both OS's as options for boot. I also must add that I had to load each OS to their respective HDD's with the other OS's HDD disconnected from the MOBO, then go into Ubuntu to modify the menu.lst file manually to get as far as I have.

 I finally have the ability to boot to both OS's after fixing some syntax in the menu.lst file, but I don't think I have the menu.lst setup properly. I am not sure if both of the HDD are booting when I choose to load XP, or if Linux is seeing the RAID array properly. I say this because when I goto "Computer" in Ubuntu, I still see the two separate drives with XP that are supposed to be in RAID 1 via MOBO software.



 I really need some help with verifying and/or fixing my installation. Just to recap, I need help verifying if the menu.lst file is correct, make sure the RAID array is booting properly when XP is chosen, make sure the device.map file is correct, and I am seeing two HDD for XP when inside of Ubuntu. Thanks in advance for any help.


 Here is the printout from the device.map file:
  (hd0)	/dev/sda
 I am assuming the others need to be added to this list?


 Here is the printout from the menu.lst file:
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
timeout		8
 ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
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
# kopt=root=UUID=cfcb1ee2-e51b-4deb-96c4-11b06011b010 ro
 ## default grub root device
## e.g. groot=(hd0,0)
# groot=cfcb1ee2-e51b-4deb-96c4-11b06011b010
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
 title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		cfcb1ee2-e51b-4deb-96c4-11b06011b010
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=cfcb1ee2-e51b-4deb-96c4-11b06011b010 ro quiet splash
initrd		/boot/initrd.img-2.6.28-16-generic
quiet
 title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		cfcb1ee2-e51b-4deb-96c4-11b06011b010
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=cfcb1ee2-e51b-4deb-96c4-11b06011b010 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic
 title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		cfcb1ee2-e51b-4deb-96c4-11b06011b010
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cfcb1ee2-e51b-4deb-96c4-11b06011b010 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
 title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		cfcb1ee2-e51b-4deb-96c4-11b06011b010
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cfcb1ee2-e51b-4deb-96c4-11b06011b010 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
 title		Ubuntu 9.04, memtest86+
uuid		cfcb1ee2-e51b-4deb-96c4-11b06011b010
kernel		/boot/memtest86+.bin
quiet
 ### END DEBIAN AUTOMAGIC KERNELS LIST
 title           Microsoft Winblows XP Pro
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd1) (hd0)
map             (hd0) (hd1)
chainloader     +1

---

