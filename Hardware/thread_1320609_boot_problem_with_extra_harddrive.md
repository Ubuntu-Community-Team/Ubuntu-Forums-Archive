---
title: "boot problem with extra harddrive"
date: 2009-11-09
forum: Hardware
---

### Post by MichaelBurns on 2009-11-09
Ubuntu 9.04 does not boot in normal mode when the slave harddrive is connected.

The desired configuration is:
- one 13 GB master harddrive with dual boot from Win98 and Ubuntu 9.04
- one 40 GB slave harddrive as storage
The Win98 boot option is nonessential; I'm just trying to smooth the transition.

Ubuntu will boot just fine when I physically disconnect the slave drive.  I can also boot into Ubuntu recovery mode with the slave drive connected.  However, when the slave drive is connected, and I select the normal Ubuntu boot, I just get a blank screen (for at least 10 minutes).

I see a screen (BIOS, I suppose) that confirms the connection of one master drive and one slave drive, so I assume that the drives are physically jumpered and connected correctly.

Any ideas how I can fix this problem so that my mom can boot the computer to Ubuntu normally with her old harddrive connected?

BACKGROUND:

My mom's Windows XP machine got badly infected.  So, I salvaged an old 13 GB harddrive (with Win98se) from an old computer, and set it up as the master in my mom's computer.  The system boots up just fine in Win98 with my mom's old 40 GB harddrive as the slave.  However, for some reason the slave drive is not visible from the Win98 filesystem.  So, I had the brilliant idea to migrate my mom over to Linux (one victory at a time).  I installed Ubuntu 9.04 on the master drive alongside Win98.  I got everything going with the slave drive NOT connected (I just wanted to be careful with it because my mom has pictures and such that she wants to save from it).

---

### Post by MichaelBurns on 2009-12-14
bump

---

### Post by SecretCode on 2009-12-14
Wild guess:

The extra drive is changing the boot drive from /dev/sda to /dev/sdb.

How do /etc/fstab and /boot/grub/menu.lst refer to the drive?

---

### Post by MichaelBurns on 2009-12-14
Thanks for the reply, SecretCode.  I will have to get back to you in a few weeks since the computer with the issue is at my mom's house a few hours away.  But now I at least have *something* to try when I visit for Christmas.

BTW, update:  I completely reformatted the 13 GB drive, so it is no longer dual boot - strictly xubuntu.  (I opted for xubuntu rather than ubuntu this time.)  However, the problem remains.

---

### Post by MichaelBurns on 2009-12-25
> **SecretCode said:**
> How do /etc/fstab and /boot/grub/menu.lst refer to the drive?They do not.

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=88b4b24b-47c3-4cf9-9711-6ae37948a434 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3616448-8bc8-4150-a156-588981d8c727 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

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
# kopt=root=UUID=88b4b24b-47c3-4cf9-9711-6ae37948a434 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=88b4b24b-47c3-4cf9-9711-6ae37948a434

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		88b4b24b-47c3-4cf9-9711-6ae37948a434
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=88b4b24b-47c3-4cf9-9711-6ae37948a434 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		88b4b24b-47c3-4cf9-9711-6ae37948a434
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=88b4b24b-47c3-4cf9-9711-6ae37948a434 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		88b4b24b-47c3-4cf9-9711-6ae37948a434
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by SecretCode on 2009-12-26
Since fstab and grub refer to the drives by uuid (which sorts out , my suggestion is not the problem. Need to look for something else...

What's the output of ```
sudo fdisk -l
``` - both with the slave drive connected and without? (Run this from a live CD if you can.)

---

### Post by MichaelBurns on 2009-12-26
I forgot my disks at home, so I was unable to run from a live cd.

Actually, anyway I was able to boot normally with the slave drive connected this time ... hmmm.

I don't know why it would've made a difference, but simply because I'm feeling impatient right now, I put the computer in suspend instead of shutdown in order to connect the slave drive.  (I'm guessing that it's bad to hotplug a harddrive, so I've always been shutting down to do these sorts of things.)  When I started it up again (unsuspended?), I got a popup error saying that something or other couldn't be mounted (most likely the slave drive), and the screen was quite glitchy.  I shutdown and then rebooted, and the computer booted all the way to the login screen, and I was able to login.

Since you asked and may be curious (and this may just be the one time that it works), here is the fdisk output:

without the slave drive connected:
```


Disk /dev/sda: 13.5 GB, 13520166912 bytes
255 heads, 63 sectors/track, 1643 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1568    12594928+  83  Linux
/dev/sda2            1569        1643      602437+   5  Extended
/dev/sda5            1569        1643      602406   82  Linux swap / Solaris

```

with the slave drive connected:
```


Disk /dev/sda: 13.5 GB, 13520166912 bytes
255 heads, 63 sectors/track, 1643 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1568    12594928+  83  Linux
/dev/sda2            1569        1643      602437+   5  Extended
/dev/sda5            1569        1643      602406   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21342133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4859    39029886    7  HPFS/NTFS

```

UPDATE:
I have been able to reboot a few times now with the slave drive connected without a hitch.  I'm going to mark this thread as (mysteriously) solved.  Thank you very much, SecretCode, for stepping up to help me on this.  I learned some useful things anyway, such as /etc/fstab and fdisk.

---

