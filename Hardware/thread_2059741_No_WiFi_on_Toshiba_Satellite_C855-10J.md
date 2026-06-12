---
title: "No WiFi on Toshiba Satellite C855-10J"
date: 2012-09-18
forum: Hardware
---

### Post by georg123abc on 2012-09-18
I just installed Ubuntu 12.04.01 on my Toshiba Satellite C855-10J laptop, but there's no WiFi.  What should I do.

PS, I'm a Terminal newbie.

---

### Post by einonm on 2012-09-19
Hi,

Firstly, how do you know there is no wifi? What does the network connection icon in the top right of the desktop report when you click on it as regards wireless connections?

Secondly, you now have a chance to use the terminal a bit more! :)

* Open a terminal, and type 'lspci' then enter. Post the output (just the line for your wifi card will do, if it's there and you can find it) - this lists the PCI devices in your system
* Also type 'lsusb' and post the output. - this lists the USB devices. Your wifi card may be on the PCI or USB bus. 
* ...and again with 'lsmod'. - This shows a list of drivers that are loaded. Hopefully the driver for your wifi card is there.

---

