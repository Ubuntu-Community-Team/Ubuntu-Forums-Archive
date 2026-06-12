---
title: "Broadcom 802.11b/g WLAN driver installation"
date: 2010-10-24
forum: Hardware
---

### Post by TheKonqueror on 2010-10-24
Hello all,
I am new to Ubuntu and only installed it last week. My WiFi card is not working because it says the driver is not available. I have followed the guide in the Documentation  at [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
However, I get stuck on the part where it says choose the .inf file for the device. I have the drivers folder, and it is full of files, how do i know which is the correct driver for my Broadcom 802.11b/g WLAN wifi card?

---

### Post by Fafler on 2010-10-24
I think you should just try them one by one. The inf file contains a PCI and Vendor ID that is matched against the actual hardware, so ndiswrapper should just refuse to use files for devices that doesn't actually exist.

---

### Post by TheKonqueror on 2010-10-25
The drivers folder is full of .sys and .dll files. There is only one .inf file, and when I tried to install it, it said invalid driver.

---

### Post by halj32 on 2010-10-25
why dont you just use the bcmwl drivers it's a lot easier. If your online just use the driver install in admin, offline the drivers are on the CD /pool
youll need to install, dkms, fakeroot, patch and then the bcmwl-kernel-source package

goodluck

---

### Post by TheKonqueror on 2010-10-27
I go to Additional Drivers in admin, but after it finishes scanning for drivers, it just says something about proprietary drivers for a modem. When i first installed Ubuntu, it gave me the same prompt and I enabled the driver. However, the WLAN card is still not working.

---

### Post by TheKonqueror on 2010-10-27
Never mind, I downloaded the driver and got it to work using ndiswrapper. You were right, the name if the driver was bcmwl.inf. Thanks!

---

