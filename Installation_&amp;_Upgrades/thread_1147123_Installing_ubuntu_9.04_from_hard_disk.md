---
title: "Installing ubuntu 9.04 from hard disk"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by colau on 2009-05-03
Hi,
I downloaded the ubuntu 9.04 and put it in windows c:\ drive.
Downloaded this "grub4dos-0.4.4".
Making a folder named "boot" in c:\ drive and inside it made another folder named grub.
Copied everything from "grub4dos-0.4.4" to c:\boot\grub.
Extracting the ubuntu.iso copied the vmlinuz and initrd.img to c:\boot

In menu.lst added this
title UbuntuInstallerlinux
kernel (hd0,0)/boot/vmlinuz
initrd (hd0,0)/boot/initrd.gz

In c:\boot.ini added this 
C:\grldr=Start GRUB


Rebooting when i select the UbuntuInstallerlinux it starts loading but after sometime it promts me saying enter 'help' for some command.
Nothing to do from there.

Would anyone please tell what to do now?

---

