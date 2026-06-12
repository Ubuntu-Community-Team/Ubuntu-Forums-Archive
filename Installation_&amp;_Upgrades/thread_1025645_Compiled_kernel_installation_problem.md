---
title: "Compiled kernel installation problem"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by titaniumdecoy on 2008-12-30
I have compiled and attempted to install a custom 2.6.28 kernel.  The problem I am having is that when I try to boot using the new kernel I get this message:

```
Begin: Waiting for root file system... ...
[    3.359063] scsi_id used greatest stack depth: 6188 bytes left
Done.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat  /proc/modules; ls /dev)
**ALERT! /dev/disk/by-uuid/778cb529-8914-451a-97ee-fb2d8ae404ae does not exist.** Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

For some reason the kernel is unable to locate my ext3 file system.

I have installed the modules via **make modules** followed by **make modules_install**.

The relevant snippet from my /boot/grub/menu.lst file is below:

```
# CURRENT WORKING UBUNTU KERNEL
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		778cb529-8914-451a-97ee-fb2d8ae404ae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=778cb529-8914-451a-97ee-fb2d8ae404ae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

# MY CUSTOM KERNEL
title		kernel 2.6.28
uuid		778cb529-8914-451a-97ee-fb2d8ae404ae
kernel		/boot/vmlinuz-2.6.28 root=UUID=778cb529-8914-451a-97ee-fb2d8ae404ae
initrd		/boot/initrd-2.6.28.img
quiet
```

I created the initrd-2.6.28.img file via the command **mkinitramfs -o initrd-2.6.28.img 2.6.28**.

I cannot figure out why the new kernel cannot locate the file system since it is using the same UUID as the working kernel.  Please help!

**EDIT:** Sometimes it complains that /lib/modules/2.6.28/modules.dep does not exist.  This file does exist.  I assume the kernel is unable to access the disk.

---

### Post by ajmorris on 2009-01-01
hi there,
i think you'll be glad to know, that it appears to not be an error with your kernel :)
The UUID identifier of your root partition has changed. So boot into a cd of linux (live or otherwise) and mount, and chroot into your ubuntu partition. Then edit /etc/fstab, and either change the UUID of your root device, to the correct one from /dev/disk/by-uuid  or, point your fstab entries to the physical block device in /dev . (i.e. /dev/sda1 etc)

If that still doesnt work, can you please post the output of:
```
sudo fdisk -l
```
```
cat /etc/fstab
```

Hope that helps,

AJ

EDIT: just noticed the menu.lst snippet... you will need to edit the ROOT= statement as well. It's easiest if that points to the physical block device, like root=/dev/sda1  (i realise that that UUID statement works for the ubuntu kernel... but an incorrect UUID is the error, so best to change fstab and root= to the physical block devices)

---

### Post by sdennie on 2009-01-02
My guess is that your initrd image doesn't have the correct modules in it.  You could verify that by typing the following at the initramfs prompt:

```

modprobe ext3

```

If you get an error, you don't have the initrd built properly.

Rather than use mkinitrd, try:

```

sudo update-initramfs -k 2.6.28 -c

```

Also, you can avoid this buy using make-kpkg instead of the normal linux kernel building method.  This is an older guide but, it should still be correct: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by ajmorris on 2009-01-02
> **vor said:**
> My guess is that your initrd image doesn't have the correct modules in it.  You could verify that by typing the following at the initramfs prompt:

```

modprobe ext3

```

If you get an error, you don't have the initrd built properly.

Rather than use mkinitrd, try:

```

sudo update-initramfs -k 2.6.28 -c

```

Also, you can avoid this buy using make-kpkg instead of the normal linux kernel building method.  This is an older guide but, it should still be correct: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

hmm, a valid point... but if it was that it couldnt load ext3, the error would be that it couldnt mount the root device, and kernel panic would be received... it wouldnt usually mention being unable to find the UUID, if this was the case...

also, @ the OP, are you using an initrd, or are you going without one?


AJ

---

### Post by sdennie on 2009-01-02
> **ajmorris said:**
> hmm, a valid point... but if it was that it couldnt load ext3, the error would be that it couldnt mount the root device, and kernel panic would be received... it wouldnt usually mention being unable to find the UUID, if this was the case...

also, @ the OP, are you using an initrd, or are you going without one?


AJ

But, if it couldn't load, for example the ATA module, you wouldn't be able to find the UUID of the root device because it wouldn't have been created.  The modprobe ext3 just the first module I knew that should be there as a quick test.  ;)

---

### Post by titaniumdecoy on 2009-01-02
I am using an initrd file.  I am using make-kpkg and dpkg to compile and install the kernel.

I finally got it working by changing the following values in my .config file.  I'm not sure which made it work.

```
CONFIG_FUSION=y
CONFIG_FUSION_SPI=y
CONFIG_SCSI=y
CONFIG_SCSI_NETLINK=y
CONFIG_BLK_DEV_SD=y
CONFIG_CHR_DEV_ST=y
CONFIG_SCSI_SPI_ATTRS=y
CONFIG_SCSI_FC_ATTRS=y
CONFIG_SCSI_ISCSI_ATTRS=y
CONFIG_SCSI_SAS_ATTRS=y
```

---

### Post by ajmorris on 2009-01-02
> **titaniumdecoy said:**
> I am using an initrd file.  I am using make-kpkg and dpkg to compile and install the kernel.

I finally got it working by changing the following values in my .config file.  I'm not sure which made it work.

```
CONFIG_FUSION=y
CONFIG_FUSION_SPI=y
CONFIG_SCSI=y
CONFIG_SCSI_NETLINK=y
CONFIG_BLK_DEV_SD=y
CONFIG_CHR_DEV_ST=y
CONFIG_SCSI_SPI_ATTRS=y
CONFIG_SCSI_FC_ATTRS=y
CONFIG_SCSI_ISCSI_ATTRS=y
CONFIG_SCSI_SAS_ATTRS=y
```

ah, most likely the SCSI options... you probably have a SCSI hard disk, without these built into the kernel (as opposed to as a module, or not at all), you cant boot the root partition.


AJ

---

