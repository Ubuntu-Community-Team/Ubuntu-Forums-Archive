---
title: "Error 17 after installing Windows Vista."
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by ggerules on 2009-02-13
Hi,

I know this is probably a common problem.... but....

- I installed Vista on my Ubuntu 8.04 laptop.
- Vista installed great and booted great.
- Now when I when back to install grub to do the dual boot thing, I did....
- Boot live cd.
- got a terminal, and typed sudo grub
- then typed find /boot/grub/stage1 which returned (**hd0,1**)
- then I typed root (hd0,1) and got no error messages.
- then I typed setup (hd0) and got.....
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists....yes
Checking if "/boot/grub/e2fs_stage1_5 (hd0)"..... 16 sectors are embedded succeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.list" ..... succeded
Done.

- Then I rebooted took the live CD out and got the following boot error message.
Failed to read splash image ((**hd0,2**)/boot/grub/splash.xpm.gz)
Press any key to continue...

- Then I pressed a key to continue

- Then I get "Error 17: Cannot mount selected partition"

Question.....

What did I do wrong?  How do I get grub to see the correct partion?

Thanks George

---

### Post by Elfy on 2009-02-13
can you post the boot list, in the livecd can you do this from a terminal

```
sudo mkdir /mnt/tmp
sudo mount - t ext3 /dev/sda2 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
blkid
```

Post the outputs please

---

### Post by ggerules on 2009-02-13
Hi,

Thanks for responding!

By typing the following.....
sudo mkdir /mnt/**tst**
sudo mount - t ext3 /dev/sda2 /mnt/**tmp**
cat /mnt/**tmp**/boot/grub/menu.lst
blkid

Did you mean .......
sudo mkdir /mnt/**tst**
sudo mount - t ext3 /dev/sda2 /mnt/**tst**
cat /mnt/**tst**/boot/grub/menu.lst
blkid

blkid didn't produce any output.......


begin cut and paste from the cat .....------------
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0875c558-88d6-41f6-8af1-b19575178f06 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1
end cut and paste ------------


Ahhh..... I think I see it now!  I need to change the all occurances of (hd0,2) to (hd0,1).  I deleted a partition in order to get vista to install.

---

### Post by ggerules on 2009-02-13
It now boots! Thanks!

George

---

### Post by Elfy on 2009-02-13
Cool - ok one you've booted you need to change one other thing you mightn't be aware of

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

Change that to (hd0,1) - lines with # aren't commented out in grub but are used.

I've changed to error :)

---

