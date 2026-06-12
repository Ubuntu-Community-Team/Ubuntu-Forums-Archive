---
title: "On dual-boot PC, no internet with XP, but Ubuntu connects fine! What gives?"
date: 2005-11-08
forum: General Help
---

### Post by Roobert on 2005-11-08
Yeah I can't connect to the internet with XP, but Ubuntu can no problem (no surprise there). I checked under My Computer/Properties/Device Manager, but all is lists for my ethernet driver is yellow question mark icons. And I don't have a driver CD, as they were factory-installed. So how can I use Ubuntu to discover my ethernet drivers?

Thanks gang! :confused:

---

### Post by matthewv on 2005-11-08
If you type in ```
lspci
``` at the terminal it will give you a list of pci devices on your system, along with specs...

---

### Post by Roobert on 2005-11-08
Ah, you rock, man. Here it 'tis:

Ethernet controller: Intel Corp. 82801BD PRO/100 VE (CNR) Ethernet Controller (rev 82)

Thanks!

---

### Post by Dr. Nick on 2005-11-08
Yeah you will have to download the appropriate drivers for you xp card in Ubuntu and copy them over somewhow. Thats one thing that Linux easily beats XP in is drivers for all devices ..except wireless.

With one exception linux has always gotten my ethernet card in all computers ive used it on, In XP I always have to load a driver cd.

---

### Post by aysiu on 2005-11-08
I'm glad it was an easy fix.

When this happens in Linux, people say it's not "ready for the desktop."
When it happens in Windows, no one says anything...

---

### Post by joris.brus on 2005-11-08
I used that lspci command
turns out it recognizes my usb as v 1.1
I know it's supposed to be v2
weird

---

### Post by xequence on 2005-11-08
That happened to me too, but I have the driver CD. Windows 2000 Datacenter Server doesent connect to the internet, even with the drivers, but ubuntu connects fine and I didnt need to manually add drivers.

---

