---
title: "Docking station not being recognised"
date: 2024-11-05
forum: Hardware
---

### Post by scorpio66 on 2024-11-05
I have just bought a ASUS Zenbook 14 UX5406S ultra 7 258v and a Kensington SD4850P USB-C Dual video driver-less dock and I'm having problems with it being recognised in Ubuntu

I have tried it in Windows 11 (I have a dual boot setup) and it works fine. If I use it with Ubuntu it hardly ever works. Occasionally it does but 95+% of the time it doesn't. I haven't been able to work out why it does occasionally work, there doesn't seem to be any pattern

I have tried turning the docking station on and off, resetting it, changing which monitors are pluged in and it still doesn't work. I've tried installing the synaptics drivers ([https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)) and deleting ~/.config/monitors.xml, logging out and trying again. Still doesn't work

Thanks you in advance

---

### Post by scorpio66 on 2024-11-06
If I do "lsusb" it shows the dock:

[FONT=Arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Arial]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=Arial]Bus 002 Device 008: ID 047d:80ac Kensington USB3.1 Hub            [/FONT]
[FONT=Arial]Bus 002 Device 009: ID 047d:80ae Kensington USB3.0 Hub            [/FONT]
[FONT=Arial]Bus 002 Device 010: ID 047d:80b0 Kensington USB3.0 Hub            [/FONT]
[FONT=Arial]Bus 002 Device 011: ID 2109:0210 VIA Labs, Inc. Hub[/FONT]
[FONT=Arial]Bus 002 Device 012: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter[/FONT]
[FONT=Arial]Bus 002 Device 013: ID 047d:806e Kensington USB Storage[/FONT]
[FONT=Arial]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Arial]Bus 003 Device 002: ID 3277:0059 Shinetech ASUS FHD webcam[/FONT]
[FONT=Arial]Bus 003 Device 003: ID 8087:0037 Intel Corp.[/FONT]
[FONT=Arial]Bus 003 Device 014: ID 047d:80ab Kensington USB2.0 Hub            [/FONT]
[FONT=Arial]Bus 003 Device 015: ID 047d:80ad Kensington USB2.0 Hub            [/FONT]
[FONT=Arial]Bus 003 Device 016: ID 046d:c548 Logitech, Inc. Logi Bolt Receiver[/FONT]
[FONT=Arial]Bus 003 Device 017: ID 047d:80af Kensington USB2.0 Hub            [/FONT]
[FONT=Arial]Bus 003 Device 018: ID 2109:2210 VIA Labs, Inc. Hub[/FONT]
[FONT=Arial]Bus 003 Device 019: ID 046d:081d Logitech, Inc. HD Webcam C510[/FONT]
[FONT=Arial]Bus 003 Device 020: ID 046d:0893 Logitech, Inc. StreamCam[/FONT]
[FONT=Arial]Bus 003 Device 021: ID 047d:808d Kensington SD4850P USB-C Dual Video Dock[/FONT]
[FONT=Arial]Bus 003 Device 022: ID 0bda:48f0 Realtek Semiconductor Corp. USB Audio[/FONT]
[FONT=Arial]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

If I go to Privacy and Security it has Direct Access turned on. Doesn't show the dock but I assume this is because this is for Thunderbolt and I'm using a USB-C dock.

[/FONT]

---

### Post by scorpio66 on 2024-11-07
I tried it with an old thunderbolt dock and this doesn't work either. Has anyone else had this issue?

---

