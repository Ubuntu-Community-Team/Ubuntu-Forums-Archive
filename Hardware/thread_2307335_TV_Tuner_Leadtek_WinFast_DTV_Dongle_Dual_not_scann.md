---
title: "TV Tuner: Leadtek WinFast DTV Dongle Dual not scanning"
date: 2015-12-24
forum: Hardware
---

### Post by petercutts1 on 2015-12-24
I am running Ubuntu 14.04 and just trying a Leadtek DTV Dual TV Tuner.

Running MyTV applications, seems to recognize it OK, and attempts to scan OK (it sits there while scanning through 50 channels), but finds nothing.
MyTV recognises my location (Australia).
I know that I have a good TV signal (using the same lead as from my TV, to an an external areal.

Tried the command "dmesg", and all the USB drivers seem there.  Any ideas on what to do next?
I am stumpted - from what I see, everything seems correct, it just doesn't work!.

Cheers


Out put from dmesg is as follows:

```

[   74.960064] usb 1-3: new high-speed USB device number 3 using ehci-pci
[   75.096125] usb 1-3: New USB device found, idVendor=0413, idProduct=6a05
[   75.096138] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   75.096148] usb 1-3: Product: WinFast DTV Dongle Dual
[   75.096156] usb 1-3: Manufacturer: Leadtek
[   75.308273] usb 1-3: dvb_usb_af9035: prechip_version=83 chip_version=02 chip_type=9135
[   75.308738] usb 1-3: dvb_usb_v2: found a 'Leadtek WinFast DTV Dongle Dual' in cold state
[   75.815139] usb 1-3: dvb_usb_v2: downloading firmware from file 'dvb-usb-it9135-02.fw'
[   77.763785] usb 1-3: dvb_usb_af9035: firmware version=3.40.1.0
[   77.763813] usb 1-3: dvb_usb_v2: found a 'Leadtek WinFast DTV Dongle Dual' in warm state
[   77.777211] usb 1-3: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   77.777476] DVB: registering new adapter (Leadtek WinFast DTV Dongle Dual)
[   77.837408] i2c i2c-6: af9033: firmware version: LINK=0.0.0.0 OFDM=3.40.1.0
[   77.837429] usb 1-3: DVB: registering adapter 0 frontend 0 (Afatech AF9033 (DVB-T))...
[   77.859775] i2c i2c-6: tuner_it913x: ITE Tech IT913X successfully attached
[   77.859791] usb 1-3: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   77.860114] DVB: registering new adapter (Leadtek WinFast DTV Dongle Dual)
[   77.884105] i2c i2c-6: af9033: firmware version: LINK=0.0.0.0 OFDM=3.40.1.0
[   77.884124] usb 1-3: DVB: registering adapter 1 frontend 0 (Afatech AF9033 (DVB-T))...
[   77.884364] i2c i2c-6: tuner_it913x: ITE Tech IT913X successfully attached
[   77.916170] Registered IR keymap rc-empty
[   77.916431] input: Leadtek WinFast DTV Dongle Dual as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/rc/rc0/input11
[   77.916883] rc0: Leadtek WinFast DTV Dongle Dual as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/rc/rc0
[   77.916902] usb 1-3: dvb_usb_v2: schedule remote query interval to 500 msecs
[   77.916915] usb 1-3: dvb_usb_v2: 'Leadtek WinFast DTV Dongle Dual' successfully initialized and connected
[   77.916994] usbcore: registered new interface driver dvb_usb_af9035
```

---

