---
title: "How to enable a PCI slot"
date: 2009-11-29
forum: Hardware
---

### Post by sunh11373 on 2009-11-29
Hi

I have just installed a video capture card (pico2000) on the 2nd PCI slot of my server. The lspci -v shows:

(the whole output is attached in a file w/ outputs from iomem, ioports and interrupts.

...

08:06.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
	Subsystem: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

08:07.0 Multimedia video controller: Brooktree Corporation Bt879(??) Video Capture (rev 11)
	Flags: medium devsel, IRQ 255
[B]	Memory at fde00000 (32-bit, prefetchable) [disabled] [size=4K]
[/B]	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 0

08:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Flags: medium devsel, IRQ 255
[B]	Memory at fde01000 (32-bit, prefetchable) [disabled] [size=4K]
[/B]	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 0

08:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ac00 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

.....

I am wondering why the pci slot 08:07.1/2 are both disabled. Is there a way I can manually enable it?

Thanks in advance.

---

### Post by sunh11373 on 2009-11-30
Update:

I found the setpci command and was able to enable the "memory" via command

 setpci -s 08:07.1 COMMAND=0002

Now I will see if I can load the bttv driver

---

### Post by sunh11373 on 2009-12-01
The bttv driver does not seem to recognize the card. See related post [http://ubuntuforums.org/showthread.php?p=8422072#post8422072](http://ubuntuforums.org/showthread.php?p=8422072#post8422072)

---

