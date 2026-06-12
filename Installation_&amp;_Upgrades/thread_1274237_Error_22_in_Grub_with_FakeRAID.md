---
title: "Error 22 in Grub with FakeRAID"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by T. N. T. on 2009-09-24
Hi guys!

I have a computer with 3 HDDs, 2x500Gb in Promise FastTrak 378 RAID mirror with Windows in the first partition and Kubuntu in second; and 1x120Gb with a Linux Boot partition and two another backup partitions.
I could install Kubuntu 9.04 in the FakeRAID array, using LiveCD and installing dmraid. I'm sure that Kubuntu is installer because I always can boot from LiveCD and see this partition.
If I boot from the RAID array I can boot to Windows and use the computer, and I want to keep this if everything corrupts I have Windows at last. So I've instaled Grub in the first partition of my 120Gb HDD from the Kubuntu installer. At this time it's not so importanting to let Grub boot to Windows because I can boot to it from the RAID array.

Sorry for asking, I am very newbie with Linux, and I get so confused to do simple things like this. My problem is everytime I try to boot to Kubuntu by running Grub from its partition, I have "Error 22". I understand that is "partition not found". I've checked with some help from internet, and seems like my grub is correctly configured. I am sending a copy of my menu.lst from grub.

Please guys! What can I do? What config I've missed from grub?

Thanks a lot!
 
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 5

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
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/pdc_bbiiadhjae2 ro

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title Debian GNU/Linux, kernel 2.6.26-2-686
root (hd0,0)
kernel /vmlinuz-2.6.26-2-686 root=/dev/mapper/pdc_bbiiadhjae2 ro 
initrd /initrd.img-2.6.26-2-686

title Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root (hd0,0)
kernel /vmlinuz-2.6.26-2-686 root=/dev/mapper/pdc_bbiiadhjae2 ro single
initrd /initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

