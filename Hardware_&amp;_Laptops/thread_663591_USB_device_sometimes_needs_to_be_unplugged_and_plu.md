---
title: "USB device sometimes needs to be unplugged and plugged in to be recognised on startup"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by monstermunch on 2008-01-10
Hi,

I have a AVerMedia AVerTV DVB-T Volar USB stick I use for watching TV under Linux (works flawlessly by the way except for this problem!). If I turn on my computer with the USB stick plugged in, it isn't recognised by Ubuntu. I know this because Kaffeine cannot see it, the blue light on the device is turned off (it turns on when loaded) and the only relevant thing I can see in dmesg is this:

> [   42.890201] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   57.982999] usb 2-1: device descriptor read/64, error -110
[   73.179674] usb 2-1: device descriptor read/64, error -110


If I unplug the device and plug it back in, it works! dmesg then contains this:

> [  324.949916] usb 2-1: new high speed USB device using ehci_hcd and address 7
[  325.082713] usb 2-1: configuration #1 chosen from 1 choice
[  325.181890] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in cold state, will try to load a firmware
[  325.218123] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[  325.900704] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in warm state.
[  325.900993] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  326.654729] dvb-usb: AVerMedia AVerTV DVB-T Volar successfully initialized and connected.
[  326.654762] usbcore: registered new interface driver dvb_usb_dib0700


The strange thing is, sometimes ubuntu recognises the USB stick first time and other times I need to use this unplug/plugin trick. I need to use this trick about 50% of the time.

I've found a lot of threads all over the place about errors like "device descriptor read/*, error -*" but few have any relevant solutions in the replies. A few have suggested blacklisting ehci_hcd with the caveat of USB1 transfer speed, but I think I need USB2 since this is TV video streams.

Does anyone have any suggestions on what I could try?

---

### Post by monstermunch on 2008-01-15
Seeing as I've had no replies, is there a better place I can ask this question? Does no-one have any idea at all what I can try?

---

