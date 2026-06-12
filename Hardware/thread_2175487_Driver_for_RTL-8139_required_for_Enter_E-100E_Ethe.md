---
title: "Driver for RTL-8139 required for Enter E-100E Ethernet Card"
date: 2013-09-19
forum: Hardware
---

### Post by Somenath_Sinha on 2013-09-19
[COLOR=#000000][FONT=Arial]I purchased an **Enter E-100E Ethernet Card**([http://www.entermultimedia.com/pci_ethernet_10_100_lancard.html](http://www.entermultimedia.com/pci_ethernet_10_100_lancard.html)) today..[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I found that ubuntu can't detect the device. So, I checked out the device driver documentation, which said :[/FONT][/COLOR][INDENT]This document contains instructions on installing Linux driver and adjusting speed for the series of RTL8139(A/B/C/8130) Network Adapter Installing Driver:
(1.) Kernel Had Supported Driver: Check the directory " /lib/modules/¡K./net " if you could find "rtl8139.o" Your kernel had supported RTL8139 series. You could easy use "linuxconf" to setup your card. If you don't like linuxconf, you also could use "modprobe rtl8139" and "ifconfig up eth0" to load module. If your driver load properly, your "/etc/conf.modules" should include line of "alias eth0 rtl8139".
(2.) Kernel Don't Support Driver: If your kernel doesn't support RTL8139 series, you should compiler driver by yourself. Please contact "www.scyld.com/network/rtl8139.html" to get source code. The compiler command is located on the end of source code. Maybe like "gcc -DMODULE -Wall -Wstrict-prototypes -O6 -c rtl8139.c". If you couldn't compiler success, maybe you should refer to error message and copy library or head file to Linux.
[/INDENT]
[COLOR=#000000][FONT=Arial]Now, (1) didn't work for me, as I did not find the said directory (after replacing the ¡K with linux-headers-3.0.8-19).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So, I tried to do (2)..[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]But, the website is down.. So, I got the source file, **rtl8139.c** from some site online.. However, when I tried to compile it with the included command, the compiler showed an error that the /usr/src/linux (or library, as the case may be) directory didn't exist..[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]However, I noticed from this site that the Realtek RTL8139 driver is quite famous.. So, I was wondering, am i missing something? Plese Help.. I'm at an dead end..[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm new to linux and Ubuntu.. So, can someone please tell me what to do... Thanks for taking the time to read this..[/FONT][/COLOR]

---

