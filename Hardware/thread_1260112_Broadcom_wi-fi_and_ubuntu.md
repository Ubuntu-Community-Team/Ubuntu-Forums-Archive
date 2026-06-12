---
title: "Broadcom wi-fi and ubuntu"
date: 2009-09-07
forum: Hardware
---

### Post by linuxrockz on 2009-09-07
Hi everyone I am recently going to purchase a laptop and have zeroed down on Lenovo G450 - 294955Q because it comes with free dos. It is having the following specifications

Intel® Core™ 2 Duo processor T6500 ( 2.10GHz 800MHz 2MB )
Operating system 	PC DOS 2000 License
System graphics 	Intel Integrated Graphics X4500
Total memory 		2 GB PC3-8500 DDR3 SDRAM 1066MHz
Display type 		14.0 " WXGA LED Backlight TFT 1366x768
Hard drive device 	320GB 5400
**Network card 		Broadcom 11b/g Wi-Fi wireless**
Optical device 		DVD Recordable (Dual Layer)
Bluetooth 		Bluetooth Version 2.1 + EDR
Finger print reader 	None
Warranty 		One year parts and labour (system battery: one year)
Pointing device 	Industry Standard Touchpad
Battery 		6 Cell Lithium-Ion

But as far as I know broadcom wireless cards don't work well under linux.
I just want to know whether the card will function under ubuntu 9.04 or not.
Please help

And thanks in advance :)

---

### Post by sergiom99 on 2009-09-08
depending on the exact model.
I can't complaint at all with mine.

It works out-of-the-box since Hardy.

---

### Post by Ayuthia on 2009-09-08
Most of the newer laptops with Broadcom wireless appear to work fine with Linux.  The Broadcom STA (the one that Broadcom made) version does have some occasional issues with using WPA/WPA2 and hidden ssid.  

I am not for sure about which chipset the Lenovo one comes with.  If you are able to test one out, you can check out the information in the property tab in the Device Manager in Windows.  It should provide a vendor/hardware id.  It will look something like 14E4:4315 where the last two digits could differ.  The 4311, 4312, 4315, 4322, and some 4328 cards work with the Broadcom STA module (wl).  The 4306, 4311, 4312, 4318, 4320, and 4324 cards will work with the Linux Broadcom (b43) module.  The 4306 and 4318 modules are the ones that are currently having the most problems but they tend to come in the older models now.

---

