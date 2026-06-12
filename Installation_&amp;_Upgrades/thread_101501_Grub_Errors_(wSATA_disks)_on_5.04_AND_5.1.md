---
title: "Grub Errors (w/SATA disks) on 5.04 AND 5.1"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by humandoing on 2005-12-09
Hi everyone, I hope someone might be able to help me with this, because I have no idea where to go anymore. This is a problem pertaining to (I am quite sure) GRUB and SATA disks, but I think that some of the problems may be Ubuntu related (Because I didn't have any problems installing Fedora Core 4). This isn't a dual-boot problem, I am NOT trying to boot Windows and Linux, or multiple versions of Windows. This is ONLY a Linux install.

Basically, the OS installs fine, without a hitch, and when the installer reboots, It drops me to a grub prompt, and the ONLY way I can get it to boot is by removing grubs "root" line, which in my case happens to be "root (hd2,0)".

Lots of details to follow.

So my hardware:
2 x 160GB SATA
1 x 120GB SATA

I've installed Ubuntu on the 120GB disk.

My "sudo fdisk -l" looks like this:


###############FDISK OUTPUT###############
```
daniel@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14338   115169953+  83  Linux
/dev/sdc2           14339       14946     4883760    5  Extended
/dev/sdc5           14339       14946     4883728+  82  Linux swap / Solaris
daniel@ubuntu:~$
```
########################################

So the details are:

/dev/sda and /dev/sdb are not really important, they are the empty 160GB disks
/dev/sdc is the disk on which I've installed Ubuntu
/dev/sdc1 is my primary partition

Here is my device.map file:

##################device.map##################
```
(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
```
###########################################

And here is my menu.lst (I've stripped the comments) - this is a big one, sorry:

#################menu.lst#################

```
default 0
timeout 3
hiddenmenu

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default
root            (hd2,0)
kernel          /boot/vmlinuz root=/dev/sdc1 ro console=tty0 quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz root=/dev/sdc1 ro console=tty0 single
initrd          /boot/initrd.img
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic Previous
root            (hd2,0)
kernel          /boot/vmlinuz.old root=/dev/sdc1 ro console=tty0 quiet splash
initrd          /boot/initrd.img.old
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic Previous (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz.old root=/dev/sdc1 ro console=tty0 single
initrd          /boot/initrd.img.old
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sdc1 ro console=tty0 quiet splash
initrd          /boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sdc1 ro console=tty0 single
initrd          /boot/initrd.img-2.6.12-10-amd64-generic
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sdc1 ro console=tty0 quiet splash
initrd          /boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sdc1 ro console=tty0 single
initrd          /boot/initrd.img-2.6.10-5-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
boot
```

##########################################

The error I get from grub when I boot is:

root (hd2,0) Selected disk does not exist.


Now, I don't know why... the device.map maps /dev/sdc to hd2, and I've tried EVERYTHING I can think of to get this to work. I simply have no idea what to do.

It _might_ be worth noting that my cdrom drive is /dev/hdc, which I thought might be conflicting with the "hd2", but I tried renaming everything in menu.lst and device.map to "hd3", and still had the same problem (I totally don't know if that's an appropriate thing to do or not).

If anyone has any ideas of how I could get this to boot properly and get GRUB configured correctly, I would be forever grateful.

Thanks a bunch.

Please let me know if you need more information.

---

### Post by markcaetano@gmail.com on 2005-12-09
if it is a compatibility problem
try an E-IDE disk (the one with the ribbon cable)
and see if that works
it might be that worm or grub or watever dosent like the sata drives

so install buntie on the e-ide and try that:rolleyes:

---

### Post by amohanty on 2005-12-10
> Now, I don't know why... the device.map maps /dev/sdc to hd2, and I've tried EVERYTHING I can think of to get this to work. I simply have no idea what to do.

[http://www.gnu.org/software/grub/manual/grub.html#Device-syntax](http://www.gnu.org/software/grub/manual/grub.html#Device-syntax)
Per the GRUB manual its fine, because the index starts from 0 and hdc is probably the secondary master, right??

This:
[http://www.gnu.org/software/grub/manual/grub.html#Device-syntax](http://www.gnu.org/software/grub/manual/grub.html#Device-syntax)
is what the root is doing for you.

Your menu.lst seems fine. There are only two things I can suggest:
1. replace root with rootnoverify
2. if that doesnt work, switch the linux drive to be the primary master hdd

Edit: SATA works fine with GRUB and ubuntu, I have two SATA Barracudas and have had no problems whatsoever.

HTH

---

