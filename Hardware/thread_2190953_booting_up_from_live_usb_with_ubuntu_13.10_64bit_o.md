---
title: "booting up from live usb with ubuntu 13.10 64bit on ASUS MAXIMUS VI"
date: 2013-11-30
forum: Hardware
---

### Post by m_ghv_geo on 2013-11-30
[COLOR=#000000]booting up from usb with ubuntu 13.10 64bit on ASUS MAXIMUS VI after the grub, purple screen comes up and on the left upper corner flashing underscore and that is it. [/COLOR]

[COLOR=#000000]SYS CONFIG [/COLOR]
[COLOR=#000000]MB: ASUS MAXIMUS VI(This problem exists on all of the verities)[/COLOR]
[COLOR=#000000]CPU: INTEL 4770K[/COLOR]
[COLOR=#000000]GPU: EVGA GTX780[/COLOR]
[COLOR=#000000]SSD: SAMSUNG 840PRO[/COLOR]

---

### Post by oldfred on 2013-11-30
At the very least you will need nomodeset with nVidia. You may need additional boot parameters also with the newest Haswell processors or some setting changes in the UEFI menu.
Are you booting with UEFI or BIOS boot mode. How you boot installer is how it installs.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

these were laptops.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)


 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

