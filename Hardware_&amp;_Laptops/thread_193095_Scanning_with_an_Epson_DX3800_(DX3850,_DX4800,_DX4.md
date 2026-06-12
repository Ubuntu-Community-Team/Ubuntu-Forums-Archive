---
title: "Scanning with an Epson DX3800 (DX3850, DX4800, DX4850...)?"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by trapanator on 2006-06-09
Hi, how can I scan with Epson DX3800 (it's same as DX3850, DX4800, DX4850...) ?

I've searched the forums but the tips I found work only with Ubuntu 5.10... (i.e. I cannot use the old hotplug system)

---

### Post by ejos on 2006-06-09
Install sane and xsane if they aren't already installed. Do a "sudo gedit /etc/sane.d/epson.conf" and make sure everything is commented out except "usb <vender code,eg 0x04b8> <product id,eg 0x0819>". Then make sure you run xsane as root and it should work. You should run sane-find-scanner to find your vender code and product id. The examples are for my Epson CX4800, it looks like this: usb 0x04b8 0x0819

---

### Post by kristalsoldier on 2007-02-27
> **ejos said:**
> Install sane and xsane if they aren't already installed. Do a "sudo gedit /etc/sane.d/epson.conf" and make sure everything is commented out except "usb <vender code,eg 0x04b8> <product id,eg 0x0819>". Then make sure you run xsane as root and it should work. You should run sane-find-scanner to find your vender code and product id. The examples are for my Epson CX4800, it looks like this: usb 0x04b8 0x0819

Hi...

I very new to all this and am running into the same problem as the original poster. Could you handhold this for me? Thanks

---

### Post by hrvooje on 2007-05-26
thank you so much! it works with my dx3850 on feisty

---

### Post by Ivo Jesus on 2007-06-12
It worked with me too, but, how can I run xsane without needing to be the root? the only way I can do this now is to run "sudo xsane", but, is there a way for me to just run "xsane" ?

---

### Post by guitarchris on 2007-06-20
Hi. I tried that but it didn't work. Evenrunning xsane as root (despite scary warning) still produces no scanner recognised.  Rummaging thru the various sane places I find all the right entries.
Running lsusb gives

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04b8:0818 Seiko Epson Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046e:5251 Behavior Tech. Computer Corp. 
Bus 001 Device 001: ID 0000:0000 

I note that the entry for epson almost corresponds to your example except for the "0x" prefix but whichever way I input the ID's it's still no go.

---

