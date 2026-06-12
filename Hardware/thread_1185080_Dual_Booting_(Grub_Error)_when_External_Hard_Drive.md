---
title: "Dual Booting (Grub Error) when External Hard Drive is Plugged in on Startup"
date: 2009-06-11
forum: Hardware
---

### Post by GilbertEvanG on 2009-06-11
Hello,
I recently purchased a HP dv7 laptop and have configured it to dual boot Ubuntu 9.04 and windows vista (came preinstalled). Vista is installed on the first hard drive, and Ubuntu is installed on a partition of the second hard drive.

Everything works great when no other hard drives are plugged in during start up. If I have an external hard drive plugged in when I try and boot, I never make it to the normal GRUB dual-booting screen. Instead I get an error (usually error 22 or 21). Once the computer has successfully booted up, I can plug in an external hard drive and it works just fine; it just doesn't let me have it plugged in when I first boot.

I have tried to do some searching before posting a new topic here, but I have had no success.

Any suggestions will be appreciated. This is the first time I have tried to dual boot, so I don't have much clue of what to do.

Thank you.

---

### Post by dandnsmith on 2009-06-12
That error is probably the 'file not found',
and is probably generated because the order of drives when you plug in the external drive before booting is not the same as grub is setup for.

I'm not enough of an expert to advise on the detail, but you could try posting the output from:
*sudo fdisk -l*
and also the details of your grub menu.1st

You could also check to see if you have the BIOS set to boot from the external HDD if it is there (if so, you could try changing that setting)

---

### Post by Bucky Ball on 2009-06-12
Switch it off at start up. Your wasting electricity if it is on and your hard drive isn't!

You need to add this drive to your fstab file so it will mount at boot. It is not recognising it because it hasn't been told it is going to be there.

---

### Post by dandnsmith on 2009-06-12
> **Bucky Ball said:**
> You need to add this drive to your fstab file so it will mount at boot. It is not recognising it because it hasn't been told it is going to be there.

Not a lot of point - by the time fstab is recognised and read the whole boot process has succeeded (or not, in which case it isn't even noticed).

---

### Post by GilbertEvanG on 2009-06-12
Thanks for the response.

Your idea that the drives are out of order is consistent with everything else I've read trying to fix this. There wasn't an option for this drive in the BIOS that I could find in the boot order section.

Here is the output of *sudo fdisk -l*:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2bf227e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28760   231008256    7  HPFS/NTFS
/dev/sda2           28760       30401    13186048    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0133bba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13055   104857600    b  W95 FAT32
/dev/sdb2           13056       30401   139331745    5  Extended
/dev/sdb5           13056       29691   133628638+  83  Linux
/dev/sdb6           29692       30401     5703043+  82  Linux swap / Solaris

```
Here is my menu.lst:
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        30

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
# kopt=root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a1683c9-f892-4586-bad6-d5cdca60b251

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



## Custom Menu ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista Home Premium
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        
root

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (recovery)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
kernel        /boot/memtest86+.bin
quiet

## ## End Default Options ##

##title        Ubuntu 9.04, kernel 2.6.28-11-generic
##uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
##kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro quiet splash 
##initrd        /boot/initrd.img-2.6.28-11-generic
##quiet

##title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
##uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
##kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro  single
##initrd        /boot/initrd.img-2.6.28-11-generic

##title        Ubuntu 9.04, memtest86+
##uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
##kernel        /boot/memtest86+.bin
##quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
##title        Other operating systems:
##root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
##title        Windows Vista (loader)
##rootnoverify    (hd0,0)
##savedefault
##makeactive
##chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
##title        Windows Vista (loader)
##rootnoverify    (hd0,1)
##savedefault
##makeactive
##chainloader    +1

```Note: I have manually edited this file to change the order of the options that show up when the computer loads. But, this problem I am having occurred before I messed with this file.

Thanks.

---

### Post by Bucky Ball on 2009-06-12
That should be hd(1,4) for the Linux install.

---

### Post by GilbertEvanG on 2009-06-12
What do you mean? Can you be more specific on what needs to be changed?

All I did to the menu.lst file was cut and paste to change the order of the items, so the actual configuration is how it was set up by default when I installed Ubuntu.

---

### Post by Bucky Ball on 2009-06-12
Here is mine (or one of them) from /boot/grub/menu.lst:

```
title           Ubuntu 8.04.2, kernel 2.6.24-24-rt
root            (hd0,5)
kernel          /vmlinuz-2.6.24-24-rt root=UUID=f6beac14-d4ec-4b90-ac38-d995a8a0acf9 ro quiet splash
initrd          /initrd.img-2.6.24-24-rt
quiet
```This is one of the examples from the start of your menu.lst:
```
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
```This is yours:

```
title        Ubuntu 9.04
**uuid        3a1683c9-f892-4586-bad6-d5cdca60b251**
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```Where you have:

```
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
```... try:

```
root        (hd1,4)
```Did you attempt to write this yourself or download it from somewhere or did that actually install?? Maybe it is a new method used in 9.04 and the newer kernel, I don't know. You might want to check this out a little more before making any changes. Just make a backup before you do.

---

### Post by GilbertEvanG on 2009-06-12
Thanks for the response.
I will try that shortly.

I didn't write it myself. All of the default stuff that the file was using (located at the end of the file) I copied to the section which I labeled "## Custom Menu ##" to change the order. I then commented out the default options at the bottom of the file.

I didn't like how it had all 5 options all jammed together so I added in divider row and renamed the titles some. But I left all of the booting options the same because I didn't want to mess that up.

So all of the booting options are how Ubuntu made them when I installed the operating system, I just renamed the titles which shouldn't make a difference.

---

### Post by GilbertEvanG on 2009-06-12
That change seemed to make a difference.

If I have my hard drive plugged in and choose "Shut Down" I am able to boot properly with the hard drive still plugged in.

But, what's kind of weird is if I have my hard drive plugged in and choose "Restart" I get the Grub error 22 when it boots up again. Hitting the power button and starting it up again (with the drive still plugged in the whole time) seems to let it boot though.

---

### Post by GilbertEvanG on 2009-06-12
This issue behaves the same way if I choose Shut Down or Restart from either Windows or Ubuntu.

Also, when I choose "Restart" from Ubuntu as opposed to "Shut Down" my speakers make a weird sound before the computer reboots.

I think the solution might be to always choose Shut Down, and never choose Restart...

---

### Post by GilbertEvanG on 2009-06-12
More info: This fix does not work with my other external hard drive. No matter how I shut down, I get the Grub error 22 if the other external is plugged in on boot up (either by itself or plugged in along side my first external)

---

