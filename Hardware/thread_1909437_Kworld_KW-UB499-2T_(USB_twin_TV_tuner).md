---
title: "Kworld KW-UB499-2T (USB twin TV tuner)"
date: 2012-01-15
forum: Hardware
---

### Post by Martyn Thompson on 2012-01-15
Bought a kworld KW-UB499-2T (USB twin TV tuner) from Maplin (UK) a couple of days ago. 

So far I haven't got it working.  It was cheap as chips so I'm not that bothered (I dual boot with Win7 so can use it on that if absolutely necessary). 

I am searching for some possible fixes on here.  The card shows up with the command ```
lsusb

1b80:e409 Afatech
```

I'm sure there will be a fix - just needs a bit of hunting for it. 

To confirm - so far it ISN'T working.

---

### Post by howefield on 2012-01-15
> **Martyn Thompson said:**
> 1b80:e409 Afatech

Have you browsed here..

[http://linuxtv.org/wiki/index.php/Kworld_UB499-2T](http://linuxtv.org/wiki/index.php/Kworld_UB499-2T)

---

### Post by Martyn Thompson on 2012-01-15
> **howefield said:**
> Have you browsed here..

[http://linuxtv.org/wiki/index.php/Kworld_UB499-2T](http://linuxtv.org/wiki/index.php/Kworld_UB499-2T)

Will have a look and report back - thanks.

---

### Post by madvinegar on 2012-01-16
Run dmesg and let us see the results.

99% there should be a line saying "firmware "bla bla bla.fw" is missing.

You should find/download this exact firmware and paste it in /lib/firmware.
Then reboot and hopefully your kworld usb will be working.

I have a similar usb dvbt (kworld 323ur) and I got it working like I explained above.
All I need to sort out now is how to activate sound. I am using TVTIME.

---

### Post by garvint on 2012-08-19
> **Martyn Thompson said:**
> Will have a look and report back - thanks.
Did you get this card working on Ubuntu?

---

### Post by sbrattonuk on 2012-12-27
I've got this tuner and have it working.
requirements were kernel 3.2 rc5 or newer.  firmware file copying over to /lib/firmware.  I used firmware v4.95 found via linuxtv.org hardware database. 

Older kernels can be used but require manual compiling and inserting of kernel modules.

---

### Post by Archfer on 2013-01-14
> **sbrattonuk said:**
> I've got this tuner and have it working.
requirements were kernel 3.2 rc5 or newer.  firmware file copying over to /lib/firmware.  I used firmware v4.95 found via linuxtv.org hardware database. 

Older kernels can be used but require manual compiling and inserting of kernel modules.

Hi, I've got this tuner and I'm having problems getting it to work. My system is a shuttle XS35 running kubuntu 12.04:

uname -r
3.2.0-35-generic

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter [GL811E]
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 002 Device 002: ID 1241:0504 Belkin 
Bus 001 Device 009: ID 1b80:e409 Afatech IT9137FN Dual DVB-T [KWorld UB499-2T]

dmesg | grep usb
[    1.001297] usbcore: registered new interface driver usbfs
[    1.001297] usbcore: registered new interface driver hub
[    1.001297] usbcore: registered new device driver usb
[    1.335594] usbcore: registered new interface driver libusual
[    1.700107] usb 1-5: new high-speed USB device number 3 using ehci_hcd
[    1.839058] usb-storage 1-5:1.0: Quirks match for vid 05e3 pid 0702: 520
[    1.839149] scsi2 : usb-storage 1-5:1.0
[    1.839350] usbcore: registered new interface driver usb-storage
[    1.840074] usbcore: registered new interface driver uas
[    1.944044] usb 1-8: new high-speed USB device number 4 using ehci_hcd
[    2.476033] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    2.682095] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    2.682379] generic-usb 0003:1241:0504.0001: input,hidraw0: USB HID v1.10 Keyboard [HOLTEK Wireless 2.4GHz Trackball Keyboard] on usb-0000:00:1d.1-2/input0
[    2.709414] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input5
[    2.710069] generic-usb 0003:1241:0504.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [HOLTEK Wireless 2.4GHz Trackball Keyboard] on usb-0000:00:1d.1-2/input1
[    2.710144] usbcore: registered new interface driver usbhid
[    2.710151] usbhid: USB HID core driver
[   37.061099] usb 1-8: reset high-speed USB device number 4 using ehci_hcd
[   37.547227] Registered led device: rt73usb-phy1::radio
[   37.547329] Registered led device: rt73usb-phy1::assoc
[   37.547429] Registered led device: rt73usb-phy1::quality
[   37.548265] usbcore: registered new interface driver rt73usb
[  145.208039] usb 1-6: new high-speed USB device number 5 using ehci_hcd
[  145.462768] usbcore: registered new interface driver dvb_usb_it913x
[  145.584217] usb 1-6: dvb_usb_v2: found a 'Kworld UB499-2T T09(IT9137)' in cold state
[  145.588756] usb 1-6: dvb_usb_v2: downloading firmware from file 'dvb-usb-it9137-01.fw'
[  147.624134] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[  149.624191] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[  151.728214] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[  153.832113] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[  155.936138] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[  158.040164] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[  158.144073] usb 1-6: dvb_usb_v2: 'Kworld UB499-2T T09(IT9137)' error while loading driver (-19)
[  158.144097] usb 1-6: dvb_usb_v2: 'Kworld UB499-2T T09(IT9137)' successfully deinitialized and disconnected
[ 1211.435126] usb 1-6: USB disconnect, device number 5
[ 1255.296040] usb 1-6: new high-speed USB device number 6 using ehci_hcd
[ 1255.552046] usb 1-6: dvb_usb_v2: found a 'Kworld UB499-2T T09(IT9137)' in cold state
[ 1255.556265] usb 1-6: dvb_usb_v2: downloading firmware from file 'dvb-usb-it9137-01.fw'
[ 1257.592128] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[ 1259.592088] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[ 1261.696183] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[ 1263.800145] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[ 1265.904116] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[ 1268.008202] usb 1-6: dvb_usb_v2: 2nd usb_bulk_msg() failed=-110
[ 1268.112077] usb 1-6: dvb_usb_v2: 'Kworld UB499-2T T09(IT9137)' error while loading driver (-19)
[ 1268.112103] usb 1-6: dvb_usb_v2: 'Kworld UB499-2T T09(IT9137)' successfully deinitialized and disconnected

I have updated v4l-dvb and downloaded the latest version of dvb-usb-it9137.fw from Linuxtv.org.

It would appear that the firmware is not being loaded but the stick works fine in Windoze7. Is there any way of checking whether or not it can be communicated with?

Any assistance would be greatly appreciated.

Archie

---

### Post by bunhead on 2013-01-24
I have a kworld UB445-U2 and from all accounts it seems that these two tuners are similar.  I have had no success in getting the 445 working under Linux.  Has there been any progress with the 499?

---

