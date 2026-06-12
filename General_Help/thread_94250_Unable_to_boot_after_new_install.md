---
title: "Unable to boot after new install"
date: 2005-11-23
forum: General Help
---

### Post by EdZ^2 on 2005-11-23
Just installed Ubuntu 5.10 on a second HDD (hdb, with windows on the first, hda), and am unable to boot up Ubuntu after installation. The error message I get is:

sh: can't access tty: job control turned off

and then a prompt. The Live CD works fine. I've tried this with other Ubuntu install discs (x64 and a 6.10 CD) and all have the same error. Mandrake has previously installed fine. Any tips on how to get it working? The bootloader I'm using is LILO, instaled to hdb (last time I tried installing GRUB or LILO to the MBR on the windows disc, it stopped wiondows from booting).

---

### Post by Xian on 2005-11-23
Just an idea but try adding this entry to the kernel line of your /boot/grub/menu.lst file:

ramdisk=8192

---

### Post by EdZ^2 on 2005-11-24
How would I go about diong this without being able to boot? (I've never been able to get the Live CD to mount partitions, but that may just be because I'm not diong the right things). Could you give me a step-by-step guide to editing the /boot/grub/menu.lst file?

::EDIT:: OK, used explore2fs to look into the /boot/ directory. There is no /boot/grub/ directory (probably because I'm using LILO instead of GRUB. The installer didn't give me the option to use GRUB.

::Further EDIT::
Problem persists after several re-installs.

---

### Post by murkin on 2005-11-25
you should be able to edit the lilo.conf file while using the live cd. i'm not very familiar with it though so... it should still be under /etc/.

explore2fs would not allow you to edit, only view.

---

### Post by EdZ^2 on 2005-11-25
Here are the contents of the lilo.conf file:

> # /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/hdb

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hdb1

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#    prompt
#    delay=100
#    timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
    label=Linux
    read-only
#    restricted
#    alias=1

    initrd=/initrd.img

image=/vmlinuz.old
    label=LinuxOLD
    read-only
    optional
#    restricted
#    alias=2

    initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#    label=HURD
#    restricted
#    alias=3
other=/dev/hda1
    label=Windows
#    restricted
#    alias=2
 Where do I add in the

ramdisk=8192

line (Or do I need to add something else)?

---

### Post by Randy Sparks on 2005-11-25
Did you opt to install an usual kernel?

---

### Post by EdZ^2 on 2005-11-25
As far as I know, yes. I just followed the default installation.

---

### Post by Scrambler on 2005-11-25
How does your system know about the Ubuntu installation of lilo did not write to your MBR? The error message you are getting is due to the fact that your boot loader cannot find a root device...

Since you're using lilo, the grub entry won't do you any good.

Anyway, if you configure lilo on the MBR on /dev/hda properly and let it know about your Windoes installation then you should be fine.

---

### Post by EdZ^2 on 2005-11-25
I booted directly from the second drive using the bios boot selector. I didn't install LILO to the MBR on /hda, as last time I tried that it trashed the MBR 9windows couldn't load).

---

### Post by sudogeek on 2005-11-30
Try this (from [http://www.weblog.nohair.net/archives/000598.html):](http://www.weblog.nohair.net/archives/000598.html):)

I assume you installed lilo when you installed Ubuntu on hdb.  If you used GRUB, then you must install lilo (see #2) to make these instructions work.

1. Boot from live CD (I use Knoppix but yu can use Ubuntu Live).

2. Mount the Ubuntu installation disk:

mkdir /mnt/ubuntu
mount /dev/hda3 /mnt/ubuntu

3. Install LILO on Ubuntu. Download the lilo package from a Ubuntu/Debian repository and copy it to /root on the Ubuntu installation (/dev/hda3/root). Now:

mount -o bind /proc /mnt/ubuntu/proc
chroot /mnt/ubuntu /bin/bash

You are now running inside the new Ubuntu installation in a bash terminal. Next, dpkg -i lilo...deb (whatever the package name is). Edit the /etc/lilo.conf file and run lilo -v -b /dev/hdb1 to put the LILO bootloader on the Ubuntu partition, assuming it is partition 1.

4. As root, type "dd if=/dev/hda3 bs=512 count=1 of=/bootubuntu.img" in the terminal. This creates a file with the first 512 bytes of the bootloader. You could copy this to a FAT floppy, a shared fat32 partition (I highly recommend this), a file server on the network, or e-mail it to yourself.

5. Now, restart into WinXP

6. Copy bootubuntu.img into C:, right alongside boot.ini.

7. Edit the 'boot.ini' file: It looks something like this:

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Add:

C:\bootubuntu.img="Ubuntu 5.10"

and save.

8. Reboot WinXP and these options should appear on the boot menu.

Good luck.

---

### Post by detyabozhye on 2005-11-30
**Many Linux distros will NOT install properly on a slave drive!**
Switch the jumpers, install, then switch them back or just run Windows as a slave, that should work.

---

### Post by EdZ^2 on 2005-12-12
> Try this (from [http://www.weblog.nohair.net/archives/000598.html):](http://www.weblog.nohair.net/archives/000598.html):)
[...]
Good luck.

I did the same thing from within windows using BootPart (copying first 512 bytes of the bootloader to the windows bootloader). This had no further effects over loading it directly from hdb from the BIOS boot loader (i.e. I get exactly the same error during boot).

I'm beginning to suspect the drive itself has died completely in a rather odd way (I originally moved it off Primary because it was getting unstable with my old windows build).

> Many Linux distros will NOT install properly on a slave drive!
Switch the jumpers, install, then switch them back or just run Windows as a slave, that should work.
I'll give this a try.

---

### Post by soapyfish on 2007-06-18
I solved this problem by pressing F6 at the first screen presented when you boot from the CD.  where you can see the options  and at the end i added  "noacpi noapic" and that solved it for me   :-)

---

