---
title: "Remove GRUB?"
date: 2008-08-29
forum: General Help
---

### Post by Newuser1111 on 2008-08-29
How can I remove GRUB from my Portable Hard Drive?
Ubuntu is not on my Portable Hard Drive anymore.

I think it says Error: 17.


And I have another question:
On my laptop's hard drive, why won't GParted be able to do anything with NTFS drives?
```
Unable to find mountpoint

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
```

---

### Post by phidia on 2008-08-29
Do you have the windows boot/install disk? you need to start up with that in the optical drive and issue "fixmbr". The way that command is used is a little different with different versions of windows. Take a look at the howto [here]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php").

---

### Post by cdtech on 2008-08-29
> How can I remove GRUB from my Portable Hard Drive?
Ubuntu is not on my Portable Hard Drive anymore.
What do you use your external drive for? (storage / OS)

---

### Post by Newuser1111 on 2008-08-29
> **cdtech said:**
> What do you use your external drive for? (storage / OS)Most of it is storage. 10-20 GB is for any OS's I want to put on it.

---

### Post by Newuser1111 on 2008-08-29
Help?

---

### Post by cdtech on 2008-08-29
Installing the GRUB bootloader writes to the first 512 blocks of the first sector. When the BIOS loads it looks for a 1 bit flag within that sector to determine if the device is bootable. You can set a partition bootable using "gparted" and maybe set it to become non bootable so that the BIOS passes this device (worth a shot but I have never done this).

You could also try overwriting the sector using the dd command (**[COLOR="DarkRed"]WARNING!!![/COLOR]** This removes the partition table, if you have data you value try the next command instead):
$ dd if=/dev/null of=/dev/sd**X** bs=512 count=1

Or just remove the MBR, without removing the partition table:
$ dd if=/dev/null of=/dev/sd**X** bs=446 count=1

Replace **X** above with your actual device, such as /dev/sda. Use fdisk -l command to find out the device name:
$ sudo fdisk -l

Hope this helps........

**Change log:**
- added the sudo command to fdisk

---

