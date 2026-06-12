---
title: "Bios/IRU Interrupt errors..."
date: 2019-07-13
forum: Hardware
---

### Post by mongo42 on 2019-07-13
Hi all,

I am trying to install Ubuntu on a Dell laptop, and am trying to verify everything BEFORE blowing away the Windows 10 OS already on there.  So, I booted into the "try before you install" version from the ubuntu install disk just to make sure that it would run, and came up with the following during boot (it did finish booting):

[B]Invalid threshold interrupt offset 1 at b 
Unexpected IRU trap at vector 7[/B]

I have no idea what these mean for the OS, or if it means that my hardware is not supported fully.  My target system is as follows (purchased from Amazon, preloaded with Windows 10):

[B]Dell Inspiron 15.6" HD Anti-Glare Laptop PC | AMD Dual-Core A6-9200 Processor | 8GB DDR4 | 128GB SSD | AMD Radeon R4 | DVD-RW | WiFi | HDMI | Bluetooth | Waves MaxxAudio | Windows 10

[/B]
Thanks for any help!

Mongo


[h=1][/h]

---

### Post by oldfred on 2019-07-13
Do not know AMD based Dell systems.
But Dell typically need UEFI update and SSD firmware update to see SSD correctly.
Drives need to be changed from RAID or Intel SRT to AHCI to see SSD.

Always fully backup Windows, even if you think you may want to remove it. Many later sell system or find one application or game that only runs in Windows & want to restore Windows.

Dell issues are common across many similar models. But AMD often different than Intel. 
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

---

### Post by mongo42 on 2019-07-13
^^^ Thank you... I thought as much.  I built my home system from scratch, so everything was at generic settings and would accept Ubuntu with no issues.  I am not so well versed in Bios specifics, so it is probably better that I don't mess with anything.... unfortunately, that means having a Windows 10 OS on my network (which, being a security/privacy nut, irks me to no end).   Back to the drawing board...  

Mongo

---

### Post by oldfred on 2019-07-13
Some systems will now update from Linux.

       UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

