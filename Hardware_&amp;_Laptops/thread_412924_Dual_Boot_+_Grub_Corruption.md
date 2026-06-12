---
title: "Dual Boot + Grub Corruption"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by Valhalla on 2007-04-18
I recently helped a friend install ubuntu on his computer, and as its his first time with linux, he wants to keep windows around incase he ever needs it for anything.
For unknown reasons, every several boots into windows, on the next reboot, Grub becomes corrupted and unable to boot. This only occurs after a reboot from windows.
In our quest to fix this, we stumbled across a discussion of Windows NT+ dynamic disks and how they may sometimes write information into the MBR. Thus, we disabled the so called Dynamic Disk Upgrade option in the windows registry, however, the problem persists.

If anyone knows what exactly windows and/or the BIOS could be doing that corrupts grub, that would be awesome. I also know that there are ways of booting Ubuntu using the windows bootloader and editing the boot.ini file, although I am unable to find any sources that describe exactly how this would be done. Either solution would work although just from an aesthetics standpoint, I would think that being able to just use grub might be easier.

Thanks all.

---

