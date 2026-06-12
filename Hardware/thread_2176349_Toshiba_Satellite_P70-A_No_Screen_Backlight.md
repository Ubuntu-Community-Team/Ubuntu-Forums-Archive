---
title: "Toshiba Satellite P70-A No Screen Backlight"
date: 2013-09-23
forum: Hardware
---

### Post by ryan37 on 2013-09-23
Trying to install Ubuntu 13. I get the CD boot screen fine. Select Install and hit Enter and the screen goes black. I originally thought the install was stalling out but under my bright desk light I noticed the install window. So I cranked up the LED on my phone and can see the install windows. I've tried all sorts of key combinations but cannot get the backlight for the screen to turn on. 

Anyone run into this before? 

Ubuntu 13.04 64b (Haven't tried with 12 but downloading it now.)
Toshiba Satellite P70-A
Intel HD4600/NVIDIA GT740M video switching

---

### Post by ryan37 on 2013-09-23
FYI. Same results with 12.

---

### Post by oldfred on 2013-09-23
Some similar Toshiba's

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

