---
title: "USB boot problems on Acer Aspire One"
date: 2010-04-23
forum: Hardware
---

### Post by NacIK on 2010-04-23
I am using a Aspire One with Windows 7 and Ubuntu 9.10. I guess something happened to my grub menu file and now it wont boot. It just boots to the grub command prompt. I tried to use UNetbootinto make a bootable SD card so that I can install Super Grub Disk and fix it, but no matter what I install on any card and boot from it on my computer it throws the prompt:

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

What now? Anyone know why it is doing this? I installed 9.04 just fine with this program and same setup before with no problems

Note: I am using the Windows version of UNetbootin from my wife's Windows 7 Aspire One.

---

### Post by oldfred on 2010-04-23
IF the BIOS is saying bootmgr is missing then the device is not bootable. Did you select the correct device. I have not tried SD cards but have used USB keys and they are listed under hard drives not USB devices.

From the command line can you manually boot? Is your install an upgrade with grub legacy or new install with grub2.

Instructions to manually boot grub2 from rescue line:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

---

