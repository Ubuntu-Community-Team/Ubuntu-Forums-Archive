---
title: "problem with webcam connected to PCMCIA USB Adapter"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by ekinsokmen on 2008-03-25
Hi,

After rebooting my laptop (pcmcia usb adapter & webcam plugged) the webcam is not recognized by ubuntu and I get the following error:
Mar 10 19:00:46 nostalji kernel: [  248.087503] pccard: CardBus card inserted into slot 0
Mar 10 19:00:46 nostalji kernel: [  248.088179] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
Mar 10 19:00:46 nostalji kernel: [  248.088241] ohci_hcd 0000:01:00.0: OHCI Host Controller
Mar 10 19:00:46 nostalji kernel: [  248.088387] ohci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 2
Mar 10 19:00:46 nostalji kernel: [  248.088468] ohci_hcd 0000:01:00.0: irq 22, io mem 0x80400000
Mar 10 19:00:46 nostalji kernel: [  248.172791] usb usb2: configuration #1 chosen from 1 choice
Mar 10 19:00:46 nostalji kernel: [  248.172955] hub 2-0:1.0: USB hub found
Mar 10 19:00:46 nostalji kernel: [  248.173025] hub 2-0:1.0: 3 ports detected
Mar 10 19:00:46 nostalji kernel: [  248.276265] PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
Mar 10 19:00:46 nostalji kernel: [  248.276343] ohci_hcd 0000:01:00.1: OHCI Host Controller
Mar 10 19:00:46 nostalji kernel: [  248.276475] ohci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 3
Mar 10 19:00:46 nostalji kernel: [  248.276550] ohci_hcd 0000:01:00.1: irq 22, io mem 0x80401000
Mar 10 19:00:46 nostalji kernel: [  248.360799] usb usb3: configuration #1 chosen from 1 choice
Mar 10 19:00:46 nostalji kernel: [  248.360966] hub 3-0:1.0: USB hub found
Mar 10 19:00:46 nostalji kernel: [  248.361034] hub 3-0:1.0: 2 ports detected
Mar 10 19:00:46 nostalji kernel: [  248.599534] usb 2-1: new full speed USB device using ohci_hcd and address 2
Mar 10 19:00:46 nostalji kernel: [  248.779540] usb 2-1: device descriptor read/64, error 8
Mar 10 19:00:46 nostalji kernel: [  249.063521] usb 2-1: device descriptor read/64, error 8
Mar 10 19:00:47 nostalji kernel: [  249.343520] usb 2-1: new full speed USB device using ohci_hcd and address 3
Mar 10 19:00:47 nostalji kernel: [  249.523512] usb 2-1: device descriptor read/64, error 8
Mar 10 19:00:47 nostalji kernel: [  249.807511] usb 2-1: device descriptor read/64, error 8
Mar 10 19:00:47 nostalji kernel: [  250.087506] usb 2-1: new full speed USB device using ohci_hcd and address 4
Mar 10 19:00:47 nostalji kernel: [  250.115131] usb 2-1: device descriptor read/8, error -71
Mar 10 19:00:48 nostalji kernel: [  250.243104] usb 2-1: device descriptor read/8, error -71
M

When I unplug the usb webcam from pcmcia adapter and plug-in again it works until next reboot. I tried to unload and reload several usb moduled (rmmod or modprobe -r) but it didn't help. 

Is there a way to fix this without physically unplugging and plugging the webcam? I use the laptop for home surveillance  and I want to be able to easily reboot it without manual interaction.

thanks.

Details:
Ubuntu 7.10 PowerPC on Powerbook G3
2.6.22-14-powerpc #1 Tue Dec 18 08:48:38 UTC 2007 ppc GNU/Linux

---

### Post by ekinsokmen on 2008-03-31
I found a workaround for this issue. 

I plugged my spare USB 1.1 usb hub to the PCMCIA USB adapter and plugged my webcam to the hub. Now the webcam is recognized also after a reboot without manually unplugging and plugging. 

The speed of USB 1.1 is not an issue for my case. This is a state I can live with.

---

