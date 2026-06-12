---
title: "cannot get  ir remote work"
date: 2020-11-30
forum: Hardware
---

### Post by caesar753 on 2020-11-30
Hello, I have a dvb-t usb stick (augustine dvb-t202) with an ir remote control. 
I'm trying to get the ir remote work but i cannot, it worked only once and i got ir codes in terminal with ir-keytable command
```

sudo ir-keytable -v -t -p rc-5,rc-5-sz,jvc,sony,nec,sanyo,mce_kbd,rc-6,sharp,xmp

```

i rebooted the pc several time and  the ir remote doesn't work any more, if I boot i windows it works.
This is my dmesg output
```

[  421.459586] usb 1-3: new high-speed USB device number 6 using xhci_hcd
[  421.612880] usb 1-3: New USB device found, idVendor=048d, idProduct=9006
[  421.612894] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  421.612902] usb 1-3: Product: USB Deivce
[  421.612908] usb 1-3: Manufacturer: ITE Technologies, Inc.
[  421.616118] dvb_usb_af9035 1-3:1.0: prechip_version=83 chip_version=02 chip_type=9135
[  421.625849] usb 1-3: dvb_usb_v2: found a 'ITE 9135(9006) Generic' in cold state
[  421.625980] usb 1-3: dvb_usb_v2: downloading firmware from file 'dvb-usb-it9135-02.fw'
[  421.733319] dvb_usb_af9035 1-3:1.0: firmware version=3.40.1.0
[  421.733342] usb 1-3: dvb_usb_v2: found a 'ITE 9135(9006) Generic' in warm state
[  421.733350] dvb_usb_af9035 1-3:1.0: [0] overriding tuner from 00 to 60
[  421.734195] usb 1-3: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[  421.734241] dvbdev: DVB: registering new adapter (ITE 9135(9006) Generic)
[  421.739010] af9033 9-001c: firmware version: LINK 3.40.1.0 - OFDM 3.40.1.0
[  421.739018] af9033 9-001c: Afatech AF9033 successfully attached
[  421.739054] usb 1-3: DVB: registering adapter 0 frontend 0 (Afatech AF9033 (DVB-T))...
[  421.742223] it913x it9133bx-tuner.0.auto: ITE IT913X BX successfully attached
[  421.753977] Registered IR keymap rc-it913x-v1
[  421.754064] rc rc0: ITE 9135(9006) Generic as /devices/pci0000:00/0000:00:14.0/usb1/1-3/rc/rc0
[  421.754153] input: ITE 9135(9006) Generic as /devices/pci0000:00/0000:00:14.0/usb1/1-3/rc/rc0/input25
[  421.754345] usb 1-3: dvb_usb_v2: 'ITE 9135(9006) Generic' successfully initialized and connected
[  421.757708] input: ITE Technologies, Inc. USB Deivce as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:048D:9006.0004/input/input26
[  421.816355] hid-generic 0003:048D:9006.0004: input,hidraw1: USB HID v1.01 Keyboard [ITE Technologies, Inc. USB Deivce] on usb-0000:00:14.0-3/input1

```

and this is ir-keytable output
```

sudo ir-keytable -v -t -p rc-5,rc-5-sz,jvc,sony,nec,sanyo,mce_kbd,rc-6,sharp,xmp
Found device /sys/class/rc/rc0/
Couldn't find any node at /sys/class/rc/rc0/lirc*.
Input sysfs node is /sys/class/rc/rc0/input25/
Event sysfs node is /sys/class/rc/rc0/input25/event19/
Parsing uevent /sys/class/rc/rc0/input25/event19/uevent
/sys/class/rc/rc0/input25/event19/uevent uevent MAJOR=13
/sys/class/rc/rc0/input25/event19/uevent uevent MINOR=83
/sys/class/rc/rc0/input25/event19/uevent uevent DEVNAME=input/event19
Parsing uevent /sys/class/rc/rc0/uevent
/sys/class/rc/rc0/uevent uevent NAME=rc-it913x-v1
/sys/class/rc/rc0/uevent uevent DRV_NAME=dvb_usb_af9035
/sys/class/rc/rc0/uevent uevent DEV_NAME=ITE 9135(9006) Generic
input device is /dev/input/event19
Opening /dev/input/event19
Input Protocol version: 0x00010001
Invalid protocols selected
Couldn't change the IR protocols
Testing events. Please, press CTRL-C to abort.

```

what's wrong?

Thanks a lot...

---

