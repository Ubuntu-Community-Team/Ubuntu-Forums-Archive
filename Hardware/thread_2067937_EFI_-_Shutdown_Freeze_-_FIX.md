---
title: "EFI - Shutdown Freeze - FIX"
date: 2012-10-08
forum: Hardware
---

### Post by wnelson on 2012-10-08
This is for those that have an system with UEFI and their system simply freezes on shutdown.

On shutdown the system will reach,

Poweroff 

then freeze.

I found that it is not any module, file system or sysctl parameters.

After trying noefi, which totally disables all of the runtime services. The boot, parameter services are still active.

1. Install *buntu as you normally do.

2. Copy the /boot/efi/efi/ubuntu/grubx64.efi to /boot/efi/efi/boot/bootx64.efi

3. In the BIO's make sure that the Hard disks is first in line in boot sequence. 

4. For this step first try adding noefi to the kernel that you want boot in the grub menu. ie, ESC, e - edit the menu item, then F10 

 if this boots successfully then Add noefi to your /etc/default/grub configuration file. GRUB_CMDLINE_LINUX="noefi"

**********************************************************************
* If at anytime you change grub or update your system and you see that 
* grub is being updated reboot and follow the first part of #4 
* temporarily removing noefi to procede with the upgrade.
**********************************************************************

5. The system should reboot and shutdown normally.

Runtime service give you the ability to get and set efi parameters, get/set time, get/set wakeup time, etc.

[http://wiki.phoenix.com/wiki/index.php/EFI_RUNTIME_SERVICES](http://wiki.phoenix.com/wiki/index.php/EFI_RUNTIME_SERVICES)

Some how the runtime service are not being handed over to linux?

---

