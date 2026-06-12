---
title: "USB Blue Yeti mic not recognized Ubuntu 14.04 LTS"
date: 2014-06-30
forum: Hardware
---

### Post by nathanmahrens on 2014-06-30
[COLOR=#000000][FONT=verdana]My USB Blue Yeti mic is not recognized when its plugged in. Other USB flash drives and such are recognized, but not my mic. I was having problems with getting my stereo headphones (akg k240) working in the back port, but got it working by installing the codecs from realtek. I don't have a clue where to begin with getting this mic to work, so any help would be greatly appreciated. P.S., I have a drive backup so if anything goes wrong, I can restore. I did plug the mic into the front USB ports as well. Thanks! -Nathan

Edit: looking into this problem via Google leads me to believe either the USB Yeti mic is completely incompatible with Ubuntu or nobody has ever ran into this kind of problem. Anything I found was related to the Yeti Pro, which connects via analog, not digital USB. I have yet to try booting into various Linux distros LiveUSB's to see if the mic is recognized in any of them. I would never move to another distro, but I am very curious as to whether the mic will work on Linux. I used the command "[/FONT][/COLOR][COLOR=#000000][FONT=monospace]lsusb --verbose | less[/FONT][/COLOR][COLOR=#000000][FONT=verdana]" and there was something that looked like an audio input.

Edit 2: After running "dmesg" I found definite traces of my mic:
[/FONT][/COLOR][    1.926247] usb 5-1.1: new full-speed USB device number 3 using xhci_hcd
[    1.945981] usb 5-1.1: New USB device found, idVendor=b58e, idProduct=9e84
[    1.945986] usb 5-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.945989] usb 5-1.1: Product: Yeti Stereo Microphone
[    1.945991] usb 5-1.1: Manufacturer: Blue Microphones
[    1.945993] usb 5-1.1: SerialNumber: REV8
[    1.947842] input: Blue Microphones Yeti Stereo Microphone as /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb5/5-1/5-1.1/5-1.1:1.3/input/input17
[    1.947938] hid-generic 0003:B58E:9E84.0005: input,hiddev0,hidraw4: USB HID v1.00 Device [Blue Microphones Yeti Stereo Microphone] on usb-0000:03:00.0-1.1/input3



[COLOR=#000000][FONT=verdana]System: Intel I5 3570K 3.4 GHz (3.8 Turbo) 
Corsair 8 GB 1600 MHz DDR3 
ASUS GTX 650 TI 1GB GDDR5 
Win 8.1 installed on: 
SSD OCZ Vertex 4 128 GB 
Ubuntu 14.04 installed on: 
SSD Crucial MX100 256 GB 
HDD 3TB Seagate Barracuda 7200RPM 6 Gb/s SATA 
CM STORM Scout Mid Tower 
Gigabyte GA-Z77X-D3H Rev 1.1 (MOBO) 
Corsair CX 600[/FONT][/COLOR]

---

