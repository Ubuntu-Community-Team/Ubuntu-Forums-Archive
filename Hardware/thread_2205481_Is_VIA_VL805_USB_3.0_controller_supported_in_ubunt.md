---
title: "Is VIA VL805 USB 3.0 controller supported in ubuntu 12.04.4?"
date: 2014-02-14
forum: Hardware
---

### Post by huike2 on 2014-02-14
I'm installing a fresh copy of ubuntu 12.04.4 on a new PC with the following hardware:

M/B: Gigabyte Ga-990FXA-UD3
CPU: AMD Athlon II X2 250 - 3.0GHz dual core
RAM: OCZ DDR3 1600MHz dual channel 2x2GB = 4GB
Storage: Apacer AH352 16GB USB 3.0 flash drive (inserted in a USB 2.0 port, because the USB 3.0 port is not  working)
VGA: Sapphire HD7950 MAC edition

Installation is pretty smooth except I have to enable an option IOMMU=Enabled in the BIOS to install ubuntu from another USB 2.0 flash drive.

The USB 3.0 controller is VIA VL805 chipset and it seems not working in ubuntu because if I insert a flash drive or a USB mouse there is no response.

My question: is VIA VL805 USB 3.0 controller supported in ubuntu 12.04.4? If not where can I find a driver for it? I have searched linux driver in Google with no luck.

Thanks for your help

---

### Post by Yellow Pasque on 2014-02-14
Have you tried disabling IOMMU after install? There are people reporting that needed to be done to enable USB 3.0 to work.

> If you add GRUB_CMDLINE_LINUX="iommu=soft" to /etc/default/grub then run the command sudo update-grub in a terminal. usb 2.0, usb 3.0, and ethernet should all work. Also don't forget to disable iommu in the bios.

[http://ubuntuforums.org/showthread.php?t=2111223](http://ubuntuforums.org/showthread.php?t=2111223)

---

