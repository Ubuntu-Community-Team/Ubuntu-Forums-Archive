---
title: "Behringer Xenyx 302USB audio interface is not recognized as audio input"
date: 2013-05-22
forum: Hardware
---

### Post by ebunders on 2013-05-22
I recently bought a Behringer Xenyx 302USB audio interface, which has a Texas Instruments PCM2902 chip. It's a  nifty little thing. The only setback is that when I plug it into Ubuntu, in the sound  settings dialogue an output device pops up, but no input device.

  For as far as I can tell the device is recognized ok. When I run lsusb, I see:

---
Bus 002 Device 004: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam Bus 003 Device 076: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth) Bus 005 Device 010: ID 08bb:2902 **Texas Instruments Japan PCM2902 Audio Codec** Bus... 
---

When I run aplay -l and arecord -l:

---
ernst@laptop-ernst:~$ aplay -l **** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]   Subdevices: 0/1   Subdevice #0: subdevice #0  ernst@laptop-ernst:~$ arecord -l **** List of CAPTURE Hardware Devices **** card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]   Subdevices: 2/3   Subdevice #0: subdevice #0   Subdevice #1: subdevice #1   Subdevice #2: subdevice #2 card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]   Subdevices: 1/1   Subdevice #0: subdevice #0
---

The usb device is listed both as record and playback device.
  So what's wrong? Any ideas, anybody?

---

