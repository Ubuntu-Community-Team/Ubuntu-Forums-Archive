---
title: "Installing to External USB Drive"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by gavinjb on 2009-08-04
Hi,

I have been playing around with the latest version of Mint through VirtualBox and have bene impressed, and I am now ready to install for real, but as my Laptop has no install disks for Windows I don't want to overwrite the OS or the boot sector of the machine, so what I am planning to do is connect a usb drive and install Mint on this and once everything is installed and configured I will swap the drive for the drive in the Laptop.

My question is, if I install on this drive do I need to do anything to make sure it writes the boot manager to this drive and not the internal disk.  Once I am installed and configured I plan on swapping this drive with my Laptops internal drive so I have this as the default OS, but during the setup process I will keep Vista as the default.

Once it is installed I can change my bios settings so that if this is connected it will boot from this disk and not the internal disk.

Gavin,

---

### Post by pizmooz on 2009-08-04
I don't have any experience with Mint in particular, but usually as long as you have the other hds disconnected  it should install the bootloader to the MBR of the drive that is the target of the install.  Also you need to make sure that the initial ramdisk that prepared by the installation includes the usb storage modules, otherwise you will be unable to mount the root partition.  I would just ask at the Mint forum and find out if anyone has done it.

---

### Post by Nessa on 2009-08-04
During the installation, there is a option to specify the location of the bootloader/grub. Just make sure that you choose a partition in the external drive that is already flagged to boot.

I run my Mint 7 off a usb drive. Works fine.

---

### Post by Mighty_Joe on 2009-08-04
> **Nessa said:**
> During the installation, there is a option to specify the location of the bootloader/grub. Just make sure that you choose a partition in the external drive that is already flagged to boot.

What he said.
After the partitioning step you will be prompted to confirm all your installation choices.  There's a button marked "Advanced" under the text box with all the choices.  Click on that and you'll be able to select the device Grub is installed on.

---

