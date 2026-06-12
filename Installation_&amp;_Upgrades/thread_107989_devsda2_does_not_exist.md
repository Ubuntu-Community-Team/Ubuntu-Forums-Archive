---
title: "/dev/sda2 does not exist"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by Hellcom on 2005-12-24
Hi, I'm new to lunix so please be easy ^_^

I'm trying to install ubuntu 5.10 on my external usb HDD, with a dell 9100. I have followed DaBruGp's great guide on how to do this, but with no luck. I have tried a few times with slight variations as I tried to figure out how to follow the instruction, and I always get the same result.

Error 17 or Error 22

The only time I seem to be close is when I manage to get the splash screen saying loading modules, however the HD becomes inactive during this to then give me this error message:

Alert! /dev/sda3 does not exist
Dropping to a shell

/bin/sh: can't access tty; job control turned off

I have one internal systems hard drive with Windows XP installed.

The usb hard drive is a Maxtor 6 L300R0 within a NexStar 3 enclosure.
[IMG]http://img.photobucket.com/albums/v608/Hellcom/54d2781b.jpg[/IMG]


[B]
Modules[/B]:

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod
# ehci-hcd
# usb-storage
# scsi_mod
# sd_mod


**initramfs.conf**:


# WAIT=12
# initramfs.conf
#

# BUSYBOX: [ y | n ]
#
# Use busybox if available.  You MUST use the -static version
#

BUSYBOX=y

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# MODULES: [ most | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# list - Only include modules from the 'additional modules' list
#
MODULES=most

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify the network device, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

# Hardcode partition to resume from so it doesn't have to be specified
# on the command line.  The command line will override this setting.

RESUME=/dev/sda5



**Menu.lst**:

##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
chainloader	+1


Can anyone help? If you need more information just ask. Thanks ^_^

---

### Post by Craig Pemberton on 2007-04-29
Hi Hellcom, welcome to Ubuntu =).

This is my situation: I had a desktop in my dorm but got a laptop instead because it took up too much room. I still have the hdd from it in an external usb enclosure. I installed Fedora on my laptop but now must have Ubuntu to work on a class project (the class uses Ubuntu). The problem is that my laptop's keyboard does not work outside of Linux (something is broken, I need to RMA it.) For the time being, that means that I cannot simply uninstall fedora and reinstall Ubuntu. I have a perfectly good Ubuntu install on my external but it's set up for ide.

I've also been using DaBruGo's thread on this. 

You can get more information on what is going on by removing splash and quiet from your menu.lst

I always get to the following point:

Begin: Waiting for root file system... ...

(usb messages)

(hangs for a full minute.)

ALERT! /dev/hda1 does not exist. Dropping to a shell!

I then get a shell with a prompt which is something like "(initramfs)"

My external is also a NexStar.

My configuration is as DaBruGo's, with the full module list.

There should be NO reference to an hd anything on my system. I'm going to check the various configs to see if i can find what wants to use it. I'm not sure how the grub device scheme works though. Anyone who knows how to do this please take a minute to help us!

- Craig

---

### Post by bulldog on 2007-04-29
Can both of you post the output of ```
sudo fdisk -l
``` to the forum?[lowercase L]
With the USB device connected and powered please.

Also can you tell me on which hdd your GRUB is in the MBR?

---

### Post by Craig Pemberton on 2007-04-29
Hey Bulldog,

Keep in mind that I have to physically remove sda (mini laptop hdd) to get it to boot to sdb (enclosure) because i have no keyboard at boot. 

Both drives have a grub in the MBR. External one is the one I care about right now.

[root@localhost ~]# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        7296    58500697+  8e  Linux LVM

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1958    15727603+  83  Linux
/dev/sdb2            1959        3916    15727635   83  Linux
/dev/sdb3            3917        5874    15727635   83  Linux
/dev/sdb4            5875       38913   265385767+   5  Extended
/dev/sdb5            5875        6135     2096451   82  Linux swap / Solaris
/dev/sdb6            6136       38913   263289253+  83  Linux

---

### Post by jome on 2007-05-02
same problem here. can not boot in linux because my CD-drive does not work, so no information. windows does see /dev/sda6 as D: drive and I can read every file on it.

---

### Post by Craig Pemberton on 2007-05-03
I hate to do this but I think I'll just take my hdd to another computer and reinstall Ubuntu. Not a perfect solution but a solution. The perfect is the enemy of the good. The shame is that I probably only need to edit one or two more files to get it working.

---

