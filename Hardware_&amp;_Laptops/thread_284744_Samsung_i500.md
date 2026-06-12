---
title: "Samsung i500"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by trhermes on 2006-10-26
I am looking for a how-to or at least a success story about syncing the Samsung i500 unit in an Ubuntu desktop environment.  

I am running Ubuntu 6.06 LTS (2.6.15.23 686 smp kernel) on an IBM thinkpad x60s.

I plugged in the cradle + i500, and cat /var/log/messages produced this:

-----------
Oct 26 01:43:47 penelope kernel: [17195486.564000] usb 1-1: new full speed USB d evice using uhci_hcd and address 2
Oct 26 01:43:48 penelope kernel: [17195487.020000] usbcore: registered new drive r usbserial
Oct 26 01:43:48 penelope kernel: [17195487.024000] drivers/usb/serial/usb-serial .c: USB Serial support registered for generic
Oct 26 01:43:48 penelope kernel: [17195487.024000] usbcore: registered new drive r usbserial_generic
Oct 26 01:43:48 penelope kernel: [17195487.024000] drivers/usb/serial/usb-serial .c: USB Serial Driver core
Oct 26 01:43:48 penelope kernel: [17195487.024000] drivers/usb/serial/usb-serial .c: USB Serial support registered for Handspring Visor / Palm OS
Oct 26 01:43:48 penelope kernel: [17195487.024000] drivers/usb/serial/usb-serial .c: USB Serial support registered for Sony Clie 3.5
Oct 26 01:43:48 penelope kernel: [17195487.024000] drivers/usb/serial/usb-serial .c: USB Serial support registered for Sony Clie 5.0
Oct 26 01:43:48 penelope kernel: [17195487.028000] visor 1-1:1.0: Handspring Vis or / Palm OS converter detected
Oct 26 01:43:48 penelope kernel: [17195487.028000] usb 1-1: Handspring Visor / P alm OS converter now attached to ttyUSB0
Oct 26 01:43:48 penelope kernel: [17195487.028000] usb 1-1: Handspring Visor / P alm OS converter now attached to ttyUSB1
Oct 26 01:43:48 penelope kernel: [17195487.028000] visor 1-1:1.1: Handspring Vis or / Palm OS converter detected
Oct 26 01:43:48 penelope kernel: [17195487.028000] usb 1-1: Handspring Visor / P alm OS converter now attached to ttyUSB2
Oct 26 01:43:48 penelope kernel: [17195487.028000] usb 1-1: Handspring Visor / P alm OS converter now attached to ttyUSB3
Oct 26 01:43:48 penelope kernel: [17195487.028000] usbcore: registered new drive r visor
Oct 26 01:43:48 penelope kernel: [17195487.028000] drivers/usb/serial/visor.c: U SB HandSpring Visor / Palm OS driver
Oct 26 01:43:48 penelope kernel: [17195487.072000] usbcore: registered new drive r cdc_acm
Oct 26 01:43:48 penelope kernel: [17195487.072000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
Oct 26 01:48:09 penelope kernel: [17195748.404000] usb 1-1: USB disconnect, addr ess 2
--------------

It seems as if the device is recongized, but I am confused as to why it would assign it to ttyUSB0, ...USB1, ...USB2, ...USB3.

I tried to use PalmOS Devices to communicate, but the program froze each time I designated the device's locality.

Help!  Anyone have any ideas or suggestions?

---

