---
title: "Can't install Ubuntu for some reason"
date: 2014-11-20
forum: Hardware
---

### Post by UncleMonty on 2014-11-20
HP Notebook PC 15
Processor Intel (R) Pentium (R) CPU N350 @ 2.16GHz 2.16 GHz
Installed Memory (RAM) 8.00 GB (7.89 GB usable)
System type: 64-bit Operating System, x64-based processor
Operating system windows 8.1

I am attempting to install ubuntu 14.04 onto this machine, however every time this fails - I cannot it seems boot the computer up in the dvd (I just get an error message telling me that windows has failed to load). What options do I have please?

(This is about the sixth computer I've tried to install ubuntu on and this is the first to resist - last time I buy anything from HP)....

---

### Post by yancek on 2014-11-20
Are you able to set the DVD to first boot priority in the BIOS?  On my HP the key on boot to access BIOS is F10, watch your screen on boot for the correct key.  Have you shut down windows 8 properly before trying to boot the DVD rather than hibernate?  Do you have Secure Boot on or off?

---

### Post by ajgreeny on 2014-11-20
If your Win8 is installed in UEFI mode, which is the default on just about all new machines, you must also install Ubuntu 64bit in UEFI mode as well. There is no way that I'm aware of that you can change the installed version of Win8 from UEFI to MBR/legacy

Ubuntu 32 bit will not work, or is very difficult to get to work, in UEFI as far as I'm aware, so why bother trying.

HP and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.

script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

---

### Post by UncleMonty on 2014-11-21
I took it back and got a refund. In future I'll do my homework before buying a laptop (I've installed linux so many times, it never occured to me that it could be a problem).

---

