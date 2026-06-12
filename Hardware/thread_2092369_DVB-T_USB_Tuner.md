---
title: "DVB-T USB Tuner"
date: 2012-12-07
forum: Hardware
---

### Post by beardedwondr on 2012-12-07
Hi, 

I've got a USB tuner that I can't seem to get to work.

lsusb:
```

Bus 005 Device 003: ID 15a4:9035 Afatech Technologies, Inc.

```dmesg:
```

[   34.729858] dvb-usb: found a 'Afatech AF9035 reference design' in warm state.
[   34.732377] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   34.732828] DVB: registering new adapter (Afatech AF9035 reference design)
[   34.733819] af9035: tuner ID=2e not supported, please report!
[   34.735764] dvb-usb: MAC address: 00:00:00:00:00:00
[   35.183297] af9033: firmware version: LINK=11.5.9.0 OFDM=5.17.9.1
[   35.183313] DVB: registering adapter 0 frontend 0 (Afatech AF9033 (DVB-T))...
[   35.185127] Registered IR keymap rc-empty
[   35.190785] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0a.0/0000:02:00.1/usb5/5-2/5-2.1/rc/rc0/input8
[   35.191227] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0a.0/0000:02:00.1/usb5/5-2/5-2.1/rc/rc0
[   35.191233] dvb-usb: schedule remote query interval to 250 msecs.
[   35.191241] dvb-usb: Afatech AF9035 reference design successfully initialized and connected.
[   35.206994] usbcore: registered new interface driver dvb_usb_af9035

```I've opened up the USB stick, the two tuner chips are AF 9033B-N2, it looks exactly the same as this: [http://linuxtv.org/wiki/index.php/MSI_DigiVox_mini_II_V3.0](http://linuxtv.org/wiki/index.php/MSI_DigiVox_mini_II_V3.0) from the outside. It's branded MobiDTV Dual, serial: MOBIDTVDUAL 150274.

Is there any chance that I can get this card working? I'm on the latest version of xubuntu (12.10).

---

### Post by Merrattic on 2012-12-08
Is your dmesg output with the stick connected from "cold" ? My afatech chipped dvb stick will only properly register from cold. Hot plugging doesn't cut the mustard.....

---

### Post by beardedwondr on 2012-12-10
For some reason i'm not getting any dvb-usb entries in dmesg now. These are the only entries that refer to the stick:
```
[ 3117.174623] usb 5-2.2: Product: DVB-T TV Stick
[ 3117.174628] usb 5-2.2: Manufacturer: ITE Technologies, Inc.
[ 3117.174633] usb 5-2.2: SerialNumber: AF0102020700001

```lsusb:
```
Bus 005 Device 005: ID 15a4:1001 Afatech Technologies, Inc. AF9015/AF9035 DVB-T stick
```

'dmesg | grep dvb-usb' shows nothing.

---

### Post by Merrattic on 2012-12-10
Turn off PC
Remove stick
Remove power cable to PC
Wait a while
Replace power cable
Insert stick
Boot up

dmesg | grep dvb
dmesg | grep DVB

---

### Post by beardedwondr on 2012-12-12
I've tried what you suggested and nothing has changed. I've just noticed that the device id seems to have changed between my first and second post.

---

### Post by Merrattic on 2012-12-13
Um, have you installed the dvb firmware drivers (system > additional drivers)

Odd about the device id change, that really shouldn't happen. Possible your stick has "two" devices (?) and only one can get picked up by the system?

---

