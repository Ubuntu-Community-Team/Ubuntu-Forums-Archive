---
title: "Kubuntu print woes"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by perlmonger on 2005-09-14
I've recently installed Kubuntu 5.04. Everything rocks except printing. I went to control center--> peripherals --> printers and selected add printer. I selected local printer parallel port #1. In the printer model selection window I selected my printer, a compaq lj1200 drv_z42. I selected the z42 because according to linuxprinting.com that is the preferred driver. Everything seems cool until I try to print a test page. The dialog box says the test page was successfully sent to printer but nothing happens. I mean nothing, no head movement no blinking of lights, no noises. Nothing. I checked the BIOS and the parrallel port is set to EPP. I'm clueless as to what to do next. Can someone help?

Update: It would appear that the cups server is neither running nor  configured. I have the following packages installed (by default)
[list]
[*]cupsys
[*]cupsys-bsd
[*]cupsys-client
[*]cupsys-driver-gimprint
[*]cupsys-driver-gimprint-data
[/list] 

Are there any more packages needed? I'm also wondering how to configure the server for local printing. I can't even find a startup script in /etc/init.d/.

Any help appreciated.

---

### Post by perlmonger on 2005-09-14
Tried re-installing previously mentioned packages. No joy.

---

