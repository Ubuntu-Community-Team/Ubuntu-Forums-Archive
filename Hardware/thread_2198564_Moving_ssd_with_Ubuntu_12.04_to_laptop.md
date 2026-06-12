---
title: "Moving ssd with Ubuntu 12.04 to laptop"
date: 2014-01-09
forum: Hardware
---

### Post by SuperFreak on 2014-01-09
Is it possible to move my desktop SSD with 12.04 installed to my laptop. I want to change the SSD capacity on the desktop to a bigger Intel SSD. Laptop is an HP Pavillion dv7-6113cl with a 2.5" hard drive (has dual boot WIN 7 and 12.04).

---

### Post by sudodus on 2014-01-09
Yes, an Ubuntu based system is portable between computers. But Windows and MacOS are not portable.

- if you have installed your system in BIOS mode, and
- you have no proprietary drivers (or uninstall them),
- the computer can manage the code (32-bit/64-bit, PC/PowerPC, need for any new proprietary driver)

Proprietary drivers are typically used for a few kinds of hardware, (graphics, wifi) and peripherals (printer ...).

---

### Post by SuperFreak on 2014-01-09
> **sudodus said:**
> Yes, an Ubuntu based system is portable between computers. But Windows and MacOS are not portable.

- if you have installed your system in BIOS mode, and
- you have no proprietary drivers (or uninstall them),
- the computer can manage the code (32-bit/64-bit, PC/PowerPC, need for any new proprietary driver)

Proprietary drivers are typically used for a few kinds of hardware, (graphics, wifi) and peripherals (printer ...).

Thanks it looks like it will work. Both 64 bit machines, no proprietary drives on desktop. The only thing I am not sure of is the desktop is a UEFI machine and the laptop a BIOS setup. Would boot repair fix GRUB Bootloader so it works with the BIOS on the Laptop?

---

### Post by sudodus on 2014-01-09
Yes it is definitely worth trying with ***Boot Repair***. Otherwise you will find a lot of good advice if you search the internet with the phrase ***ubuntu grub2***

---

### Post by tgalati4 on 2014-01-09
You may have to change the Block ID in both grub2 configuration file and in /etc/fstab.  They need to match the Block ID of the new drive/partition.

tgalati4@Mint14-Extensa ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
**UUID=b9e5433e-791c-4c7a-b08c-62f6820a474f** /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
**UUID=1c9e07eb-1f94-435f-94be-38f74c0ff1e0** none            swap    sw              0       0
tgalati4@Mint14-Extensa ~ $ blkid /dev/sda3
/dev/sda3: **UUID="b9e5433e-791c-4c7a-b08c-62f6820a474f"** TYPE="ext4"

tgalati4@Mint14-Extensa ~ $ sudo blkid /dev/sda4
/dev/sda4: **UUID="1c9e07eb-1f94-435f-94be-38f74c0ff1e0"** TYPE="swap"

Boot repair might take care of this, but it's easy enough to check and change manually.

---

### Post by SuperFreak on 2014-01-10
Right. Editing fstab should be easy enough

---

