---
title: "Old UUID hanging around somewhere after harddrive upgrade"
date: 2008-05-30
forum: Hardware
---

### Post by theophile on 2008-05-30
I replaced the SATA drive in my laptop and put the old drive in a USB enclosure for a nice portable drive. However, even after changing the UUID to the new hard drive in /etc/fstab AND /boot/grub/menu.1st, I still cannot boot the system unless the OLD drive is connected via USB.

Here's my menu.1st:

```
root@graven:/boot/grub# cat menu.lst
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
default 0

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a97369f0-7d64-4ced-82ec-88bbab3f0059 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 8.04, kernel 2.6.24.3
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24.3 root=UUID=a97369f0-7d64-4ced-82ec-88bbab3f0059 ro quiet splash
initrd          /boot/initrd.img-2.6.24.3
quiet

title           Ubuntu 8.04, kernel 2.6.24.3 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24.3 root=UUID=a97369f0-7d64-4ced-82ec-88bbab3f0059 ro single
initrd          /boot/initrd.img-2.6.24.3

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=a97369f0-7d64-4ced-82ec-88bbab3f0059 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=a97369f0-7d64-4ced-82ec-88bbab3f0059 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I've done the following to reinstall GRUB, which appears to happen successfully:
```
grub
root (hd0,1)
setup (hd0)
quit
```

Even still, here's the beginning of dmesg ouput:
```
[    0.000000] Linux version 2.6.24.3 (root@graven) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #3 SMP $
[    0.000000] Command line: root=UUID=651d2207-a689-4ebe-9bd4-dff0c5782f15 ro quiet splash

* * *

[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 31584 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 483102
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=651d2207-a689-4ebe-9bd4-dff0c5782f15 ro quiet splash
[    0.000000] Initializing CPU#0
```

As you can see, the kernel lines *still* reference the old drive's UUID.

What do I have to do here?

Thanks!

---

### Post by logos34 on 2008-05-30
maybe the Bios hard disk boot order is set to boot external first and internal second?  switch it if that's the case

---

### Post by theophile on 2008-05-30
This occurs without the USB drive attached at all. In fact, the boot process hangs indefinitely until I attach the USB drive, at which point the boot continues (off the USB drive) normally. Even so, the filesystems on the internal drive are mounted.

For some reason, GRUB is explicitly calling the old drive by UUID and I can't change it.

---

### Post by theophile on 2008-05-30
I manually wiped the MBR with this:
```
dd if=/dev/null of=/dev/sda bs=446 count=1
```

and reinstalled GRUB. It is *still* calling the old UUID on the kernel command line.

I downloaded the SuperGRUB Disk and booted off that. It asked for the location of my stage2 and menu.1st files, which I gave it, both from /boot/grub.

It ***STILL*** called the old UUID.

Is the UUID of the boot partition hardcoded in stage2 or something? How is that file generated?

This is driving me mad!

---

### Post by logos34 on 2008-05-30
I understand your exasperation...Very odd, never encountered this before

---

### Post by theophile on 2008-05-30
.... I found the problem.

I still don't have an explanation for why this happened, but it's fixed now.

Apparently, even though 'mount' showed that /dev/sda2 was mounted at /, it was actually mounting /dev/sdb2 there. So all the modifications I was making to /boot/grub/menu.1st were actually being made on the USB drive, not the internal drive.

There was actually a point where 'mount' showed /dev/sda2 and /dev/sdb2 both mounted in different locations, but changes to one location were mirrored to the other.

I solved it by booting off the LiveCD, mounting /dev/sda2 locally, and changing the menu.1st file from there. That did it. Thank God.

---

### Post by DizzyTech on 2008-05-30
I think you need to update the init file system cache (I think that's what it is).  What you need to run in the system is:
```

sudo update-initramfs -u

```

Also, make sure the /etc/fstab references the new drive.  There could also be some ACPI files hanging around that reference your old drive for suspend/hibernate.

---

