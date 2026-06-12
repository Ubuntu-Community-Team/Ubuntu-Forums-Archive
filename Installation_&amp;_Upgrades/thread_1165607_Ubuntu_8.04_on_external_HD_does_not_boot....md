---
title: "Ubuntu 8.04 on external HD does not boot..."
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by s05128 on 2009-05-20
Hi guys, hopefully someone can help me before I kill myself due to frustration...

ok, here goes:

1. I want to make a portable persistent external USB HD on my **80G** external HD

2. My CDROM is broken therefore Live CD is no good, that been said, I have created a "USB LiveCD" on my 8G **flash **drive

3. Removed my internal HD, changed my BIOS boot sequence to USB, got the "USB LiveCD" working, installed on my external HD (not flash drive), installed boot loader to my 80 external HD in the Advance option of the last step of installation... blah blah

4. Restarted without my internal HD, and... nothing... gives me:
"No boot sector on the USB device". When I put my internal HD back, it just loads to Windows... help...

I'm stuck for a few hours here, hopefully you can help me, thanks a lot!!!

**here goes my *sudo fdisk -l* when I was in LiveCD:**

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 8019 MB, 8019509248 bytes
175 heads, 32 sectors/track, 2796 cylinders
Units = cylinders of 5600 * 512 = 2867200 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2797     7831535+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82f3fbdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


**and the menu.lst if needed:**

ubuntu@ubuntu:~$ sudo cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=e8f1a5a1-6ccd-4857-8b47-2c02ac3909aa ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e8f1a5a1-6ccd-4857-8b47-2c02ac3909aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e8f1a5a1-6ccd-4857-8b47-2c02ac3909aa ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by utnubuuser on 2009-05-20
I assume your BIOS is set to boot from USB?  Most BIOS' are set to not boot from USB by default.

And have you tried installing the OS with/without setting an actual /boot partition?

---

### Post by Ptero-4 on 2009-05-20
Can you reinstall with the internal HD installed? That way grub will forcibly set itself to /dev/sdbx (hd1,x). Your menu.lst shows that grub have all the entries set to (hd0,x) (/dev/sdax) and it won't work because when you put the internal HD back in the block device letters go from sda (it was set like that because the installer detected only one disk) to sdb (which happens because now there are two disks and the internal takes precedence moving the external to sdb).

---

### Post by s05128 on 2009-05-21
> **Ptero-4 said:**
> Can you reinstall with the internal HD installed? That way grub will forcibly set itself to /dev/sdbx (hd1,x). Your menu.lst shows that grub have all the entries set to (hd0,x) (/dev/sdax) and it won't work because when you put the internal HD back in the block device letters go from sda (it was set like that because the installer detected only one disk) to sdb (which happens because now there are two disks and the internal takes precedence moving the external to sdb).

Thanks for your response, the problem is that it won't even work when i restart without my internal HD in the device. So according to what you said, BIOS would still recognize its only HD (the USB removable one) as sda. Please correct me if i am wrong.
I'm going to reinstall ubuntu with the internal HD connected and see how things will go.
Thanks :)

---

### Post by s05128 on 2009-05-21
> **utnubuuser said:**
> I assume your BIOS is set to boot from USB?  Most BIOS' are set to not boot from USB by default.

And have you tried installing the OS with/without setting an actual /boot partition?

Yes I have set my BIOS to boot USB 1st.
how do i install the OS with/without setting /boot partition and why would i do that?
please forgive my shallow knowlegde on linux... still learning hehe

---

### Post by utnubuuser on 2009-05-23
/boot is a seperate partition.  If you do a guided install of Ubuntu, it'll put grub in /    Don't forget to make a seperate /home partition.

---

