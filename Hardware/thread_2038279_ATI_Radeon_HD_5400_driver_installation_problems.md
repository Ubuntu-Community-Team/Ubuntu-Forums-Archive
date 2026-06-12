---
title: "ATI Radeon HD 5400 driver installation problems"
date: 2012-08-06
forum: Hardware
---

### Post by propercoil on 2012-08-06
I'm trying to install a driver for my graphic card on 12.04.
when i go to "System Test" it says "VESA graphic not in use" and System-> Hardware says the graphic driver is "unknown".
invoking "lspci | grep VGA" gives:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]

I followed the suggestions of this [work-through]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") trying to install with "Additional Drivers". it did install and said the driver is active but after rebooting and invoking "fglrxinfo" i got multiple errors:

X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  136 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  12
Current serial number in output stream:  12

tried to use the suggestions from [this thread]("http://askubuntu.com/questions/81344/how-to-fix-error-with-ati-driver-error-of-failed-request") with no luck.

I then tried to install the propriety driver from amd following [this tutorial]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers") but nothing works and when rebooting you get a message saying ubuntu running on low graphics, catalyst crashes every time. now i'm stuck trying to uninstall fglrx with the errors:

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

[sudo] password for propercoil: Reading package lists... Done Building dependency tree
Reading state information... Done Virtual packages like 'xorg-driver-fglrx' can't be removed E: Unable to locate package fglrx_8.980-0ubuntu1_i386.deb E: Couldn't find any package by regex 'fglrx_8.980-0ubuntu1_i386.deb' E: Unable to locate package fglrx- amdcccle_8.980-0ubuntu1_i386.deb E: Couldn't find any package by regex 'fglrx- amdcccle_8.980-0ubuntu1_i386.deb' E: Unable to locate package fglrx-dev_8.980- 0ubuntu1_i386.deb E: Couldn't find any package by regex 'fglrx-dev_8.980-0ubuntu1_i386.deb'

I have spent over 15 hours total trying to resolve this, i'm about to hang the towel and go back to windows. i love the flexibility ubuntu has being a web dev but this is crazy. if only i had a remedy to the ati nonsense. i think i'm just frustrated?

---

### Post by jemadux on 2012-08-06
go to bios and choose to work with intel .. perharps intel hd driver works fine with Linux

---

### Post by Ubun2to on 2012-08-06
> **jemadux said:**
> go to bios and choose to work with intel .. perharps intel hd driver works fine with Linux

Are they Intel HD graphics? I know Ivy Bridge works with Linux-I'm using Ivy Bridge on my laptop.

---

