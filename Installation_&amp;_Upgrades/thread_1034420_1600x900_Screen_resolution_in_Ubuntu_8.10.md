---
title: "1600x900 Screen resolution in Ubuntu 8.10"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2009-01-08
Just installed Ubuntu 8.10 on a new sony laptop with 16.4 inch screen. The screen's resolution should be 1600X900 aspect ratio 16:9
I've gone to system>preferences>screen resolution but only have two options there 800X600 and 640X480 how can I set this right?

---

### Post by kranny on 2009-01-08
Did you install the Video Drivers of your Chipset.Try to post the output of ```
lspci
```

---

### Post by niceguy123 on 2009-01-08
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

```

---

### Post by niceguy123 on 2009-01-09
Can some one help me configure the resolution to 1600X900

Thanks.

---

### Post by kranny on 2009-01-09
Intrepid already ships with the 2.4.1 Intel driver.So need to install anything new..If you're limited to a 800x600 resolution , then you're probably using the (generic) VESA driver. You should attach your /var/log/Xorg.0.log..

Your video chipset is just new..Btw this guide elps you to an extent
[http://www.claudiocamacho.org/tech/sr11m_debian.php](http://www.claudiocamacho.org/tech/sr11m_debian.php) 

which gives you the xconf.org settings required to get 1280x800 resolution using the vesa drivers.

---

### Post by niceguy123 on 2009-01-10
> **kranny said:**
> Intrepid already ships with the 2.4.1 Intel driver.So need to install anything new..If you're limited to a 800x600 resolution , then you're probably using the (generic) VESA driver. You should attach your /var/log/Xorg.0.log..

Your video chipset is just new..Btw this guide elps you to an extent
[http://www.claudiocamacho.org/tech/sr11m_debian.php](http://www.claudiocamacho.org/tech/sr11m_debian.php) 

which gives you the xconf.org settings required to get 1280x800 resolution using the vesa drivers.

Thanks for the lead to this information. I briefed though it and saw that is very tec for me and I wouldn't want to start making changes in my configurations only to learn that it wasn't meant for the make of my laptop. I am working on Sony Vaio, but, mine is 1600X900 not 1280X800

Aside for that can you help me with the the log you suggested I attach, how do I get that log? 

Thanks,

---

### Post by niceguy123 on 2009-01-16
Can someone help me make this easy. I don't want to make a wrong move and be stuck with no screen.

---

