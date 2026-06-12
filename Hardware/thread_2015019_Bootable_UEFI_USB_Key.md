---
title: "Bootable UEFI USB Key"
date: 2012-07-02
forum: Hardware
---

### Post by fleamour on 2012-07-02
All boot disks seem to be traditionally legacy.  UEFI is fairly recent.  Setting my laptop to legacy boot only, will boot Parted Magic from USB key but not my OS.  Setting dual boot order to legacy first then UEFI, does not have the desired effect.  A happy medium is to hit F12 then choose boot device from list.  Auto booting fails to detect USB key completely.

What advantages are there to UEFI over GRUB Legacy?  

Also, is there a handy UNetbootin like (preferably multi image boot) GUI creation tool that can handle creating a UEFI bootable USB stick?

I can only imagine this fragmentation is a IT support headache, assuming all UEFI implementations are as bad as my ThinkPad Edge.  Seriously, no fancy graphics & USB keys do no boot either.

Which ever way you look at it, there is no longer one key to rule them all!

---

### Post by wnelson on 2012-07-02
Create a usb key with fat16 and then create the following:

/EFI/boot

Get the shell.efi (it sounds like you need the older shell.efi because it supports older versions of EFI specs.)

cp shell.efi to /EFI/boot/boot.efi for 32bit/ bootx64.efi 64bit.

That should work correctly with usb legacy enable in the bios.

You can also take the file /boot/efi/EFI/ubuntu/grubx64.efi and copy it to /boot/efi/EFI/boot/boot.efi and it will boot you system. Make sure that press F12 and select your hard drive not ubuntu. 

Walt.

Arch linux has a really good explanation of efi booting.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

---

### Post by fleamour on 2012-07-11
Thanks!  I will definitely try the above.

:biggrin:

---

