---
title: "Hauppage HVR 850"
date: 2008-12-17
forum: Hardware
---

### Post by rick71 on 2008-12-17
I am trying to het an HVR 850 working. I am using 8.10, updated.
I have placed dvb-fe-xc5000-1.1.fw into /var/firmware. I have loaded em28xx, em28xx device_mode=1, and em288-dvb.

dmesg shows:
[   22.861483] tveeprom 0-0050: Hauppauge model 72301, rev B3F0, serial# 5090793
[   22.861509] tveeprom 0-0050: MAC address is 00-0D-FE-4D-AD-E9
[   22.861532] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 4)
[   22.861554] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   22.861582] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[   22.861603] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[   22.861632] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   22.861668] hauppauge_eeprom: hauppauge eeprom: model=72301
[   23.035633] xc5000: Successfully identified at address 0x61
[   23.035650] xc5000: Firmware has not been loaded previously
[   23.035760] DVB: registering new adapter (au0828)
[   23.035897] DVB: registering frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   23.038191] Registered device AU0828 [Hauppauge HVR850]
[   23.038309] usbcore: registered new interface driver au0828
[   23.343151] usbcore: registered new interface driver snd-usb-audio

However, when I start xawtv i get:

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1024x768+0+0
WARNING: No DGA support available for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

Can anyone see what might be wrong? any and all help appreciated.

---

