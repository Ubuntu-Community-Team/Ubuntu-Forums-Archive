---
title: "anyone have any luck with the hvr950q?"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by tigerstripedcat on 2008-12-12
For the life of me I can't get the hvr950q usb tvtuner to work. The problem is when I try and scan for channels: 

```
$ sudo ./w_scan
w_scan version 20081106
Info: using DVB adapter auto detection.
   Wrong type, ignoring frontend /dev/dvb/adapter0/frontend0
main:2762: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

```

I copied the firmware to /lib/firmware/2.6.27-9-generic/dvb-fe-xc5000-1.1.fw

And it seems to detect:

```
[36180.115653] usb 3-1: new high speed USB device using ehci_hcd and address 6
[36180.295198] usb 3-1: configuration #1 chosen from 1 choice
[36180.658854] au0828: i2c bus registered
[36180.758710] tveeprom 1-0050: Hauppauge model 72001, rev B3F0, serial# 4759833
[36180.758725] tveeprom 1-0050: MAC address is 00-0D-FE-48-A1-19
[36180.758730] tveeprom 1-0050: tuner model is Xceive XC5000 (idx 150, type 4)
[36180.758736] tveeprom 1-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[36180.758740] tveeprom 1-0050: audio processor is AU8522 (idx 44)
[36180.758745] tveeprom 1-0050: decoder processor is AU8522 (idx 42)
[36180.758749] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[36180.758754] hauppauge_eeprom: hauppauge eeprom: model=72001
[36180.775031] xc5000 1-0061: creating new instance
[36180.778324] xc5000: Successfully identified at address 0x61
[36180.778332] xc5000: Firmware has not been loaded previously
[36180.780644] DVB: registering new adapter (au0828)
[36180.781535] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[36180.783786] Registered device AU0828 [Hauppauge HVR950Q]

```

I don't see a single error.  I've also tried installing the bleeding edge v4l drivers from [http://www.linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://www.linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)

The chipset is an xc5000, and the module is loaded

```

$ lsmod | grep xc5000
xc5000                 19464  1
i2c_core               31892  7 asb100,xc5000,au8522,au0828,tveeprom,nvidia,i2c_viapro

```

I've found places where people say they got this thing working, but I don't know what's going on.

Thanks!
TSC

---

