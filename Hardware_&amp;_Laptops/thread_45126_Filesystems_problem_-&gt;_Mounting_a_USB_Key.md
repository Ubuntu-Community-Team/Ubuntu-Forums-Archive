---
title: "Filesystems problem -&gt; Mounting a USB Key"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by Cervantes on 2005-06-28
Hello all.  I've started with Ubuntu but am havign grave difficulty.  I can't seem to mount my usb flash drive.  
I've added /dev/sda1 to my /etc/fstab file, as such:
```
/dev/sda1    /media/usb    vfat    rw,user,auto    0    0
```
When I try to mount it (as such:
```
sudo mount -t vfat /dev/sda1 /media/usb
```
I get the following:
```

mount: wrong fs type, bad option, bad superblock on /dev/sda1, or too many mounted file systems (aren't you trying to mount an external partition, instead of some logical partition inside?)

```

This is, however, after I followed the advice here: [http://www.ubuntuforums.org/showthread.php?t=42599&highlight=usb+mount](http://www.ubuntuforums.org/showthread.php?t=42599&highlight=usb+mount)
I did this:
```
modprobe -r ehci-hcd
```

Before doing that, I receieved a message something like such, when trying to mount my usb key:
```
mount: blah blah blah (forget) does not exist
```

dmesg looks something like this (I can't copy and paste it because I've got two seperate computers going here.  Long story...):
```

lots of stuff that's probably not of interest
scsi0 : SCSI emulation for USB Mass Storage devices
  Vendor: Kingstron  Model: DataTraveler 2.0   Rev: 1.00
  Type :    Direct Access                                     ANSI SCSI revision: 02
USB Mass Storage device found at 2
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
SCSI device sda: 974848 512-byte hdwr sectors (499 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through /dev/scsi/host0/bus0/target0/lun0: [CUMANA/ADFS] pl<5>Attached scsi removable disk sda at scs0, channel 0, id 0, lun 0

Then there's  a bunch of lines like this:
Buffer I/O error on device sda1, logical block <508378384 .. 508378399>

Next, there's a bunch of lines like this:
FAT: invalid media value (0xb9)
VFS: Can't find a valid FAT filesystem on dev sda1.

Then:
NTFS driver 2.1.15 [Flags R/O MODULE].
NTFS-fs error (device sda1): read_ntfs_boot_sector():Primary boot sector is invalid.
NTFS-fs-error (device sda1):read_ntfs_boot_sector(): Mount option errors=recover not used.  Aborting without trying to recover.
NTFS error (device sda1):ntfs_fill_super(): Not an NTFS volume.
FAT: invalid media value (0xb9)
VFS: Can't find a valid FAT filesystem on dev sda1

```

Aah, that was a lot of typing.   ](*,)  Anyone have any suggestions?
Thanks in advance!

---

### Post by fabiand on 2005-06-29
seems as if there is a ntffs filesystem on the usb stick, if you dont need the data on the usbstick do the following:

**[COLOR=Red]ALL YOUR DATA WILL BE LOST![/COLOR]**

unmount the usbstick

```

sudo mkfs.vfat /dev/sda1

```

now plug the stick out and back in.

hopefully youve got an empty usbstick now, which is recognized by windows and linux.

fabiand

---

### Post by Cervantes on 2005-06-30
Thanks for the reply.  I've checked my USB key in my Windows XP machine and it says it is a FAT filesystem.  
When I tried your advice, I got this:
```

mkfs.vfat 2.10 (22 Sep 2003)
mkfs.vfat: Attempting to create a too large file system

```
Umm.. it's 512mb.   :-? 

Thanks again,
Cervantes

---

### Post by Cervantes on 2005-07-08
I must say I'm rather disappointed.  If I can't get things like this working, I'm going to have to stay away from linux.
That said, I've tried formatting my usb key to both FAT and FAT32 (it was FAT before).  I've updated /etc/fstab to suit the changes (when it was FAT, I had the fs type as "vfat".  When it was FAT32, I had the fs type as "vfat32", though it said it does not support that fs type).  I get the same error messages.  mkfs.vfat /dev/sda1 does not work with the same error message.

If anyone can help, I would be very grateful.  If not, I guess I'll be sticking with Windows then...

---

### Post by snipes420 on 2005-09-26
did you try the filesystem type msdos?
> mount -t msdos /dev/sda1 /media/usbdisk
some of my windows partitions I can mount with this type.

---

