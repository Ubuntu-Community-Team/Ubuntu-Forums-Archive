---
title: "Texas Instruments card reader in Toshiba A105"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by hsalgado on 2007-11-21
Hi, I have the internal card reader working randomly.  When I updated to Feisty it started working (didn't work in Edgy).  Then, after an "umount" it stopped working.  I have tried several ideas in the post and no one seems to work, until today I plug a generic card reader and... magically it worked again!  But just until I rebooted the system... I am not sure if it worked because there was some driver I installed or because I pluged the USB generic card reader...

This is the result of lspci:

07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

I really need that reader working, please let me know if you have any idea to check what the problem could be.  Is there any way I can reinstall Feisty to its original state?

Thanks a lot for any help.

---

