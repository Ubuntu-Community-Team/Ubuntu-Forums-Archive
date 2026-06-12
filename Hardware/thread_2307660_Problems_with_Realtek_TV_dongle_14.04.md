---
title: "Problems with Realtek TV dongle: 14.04"
date: 2015-12-27
forum: Hardware
---

### Post by Bucky Ball on 2015-12-27
Hi all,

Bit of an odd one. About two weeks ago I cloned the 14.04 OS on my hard drive to an internal SSD. It all works perfectly and seems to be identical in every way, except ...

I have an Ezycap USB TV dongle which, in the hard drive install, works out of the box (which it has since 14.04 for me, 12.04 took a bit of stuffing around, but I did get it to work there just fine too). 

On the cloned copy of the install on SSD, plug it in, run dmesg, and get this regarding the TV tuner dongle:

```
[  834.236016] usb 2-1.3: new high-speed USB device number 4 using ehci-pci
[  834.335018] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=2838
[  834.335024] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  834.335028] usb 2-1.3: Product: RTL2838UHIDIR
[  834.335031] usb 2-1.3: Manufacturer: Realtek
[ 1669.254541] perf samples too long (2506 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2064.891657] usb 2-1.3: USB disconnect, device number 4
[ 2071.210167] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[ 2071.299454] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=2838
[ 2071.299461] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2071.299464] usb 2-1.3: Product: RTL2838UHIDIR
[ 2071.299467] usb 2-1.3: Manufacturer: Realtek
```

As you can see, recognises but doesn't install a driver or configure the device (this does happen and is reflected in dmesg output when dongle plugged in in the hard drive install). 

I use MeTV in the hard drive install with the card and that all works fine, TV no problem. Launch MeTV in the SSD install, and naturally, I get something along the lines of 'No dvb device detected'. 

Not sure what's happened here a) because this is, or at least I thought it was, an identical copy of the HDD install so was expecting the dongle and MeTV to co-operate fine, and b) this device has always worked 'out of the box' with 14.04 in the past, at least for me (and on the strength of this I bought another for a friend a couple of months ago when I spotted it tucked away on a shelf in a dusty computer store). 

I'll boot into the HDD install and give the dmesg output for the dongle from there if required, just ask. For now, any ideas about what's happening? Have I missed something obvious (not unusual!) TIA. :)

Puzzled (also not unusual). :-k

PS: The HDD install appears to be using dvb_usb_rtl28xxu, if that is a driver, and identifies the dongle as 'realtek rtl2832u'.

---

### Post by matt_symes on 2015-12-27
Hi BuckyBall.

This sounds almost like udev is not being triggered when the device is plugged in, when run from the external SSD.

So we can see a comparison:  boot into each install (from both the internal hard drive and the external SSD), open a terminal in each and type

```
udevadm monitor
```

Plug the tuner in and post the output back here from the two boots.

I don't use a USB TV tuner (actually i don't watch broadcast TV at all anymore), but we may be able to track down where the problem area is or someone else may see this post and chime in.

**EDIT:**

BTW: Is the SSD USB2 or 3 ?

Kind regards

---

### Post by Bucky Ball on 2015-12-28
Thanks for the input. I'll try these things shortly.

Just to reiterate: The SSD is internal. Toshiba Satellite Pro L510 laptop. Pulled optical drive bay out and put hard drive bay in its place (you can get ones that fit in the optical drive bay), so it is is SATAII I would think (this machine not SATAIII). But yes, it is seen as sdb.

This is from the SSD install (sdb):

```
$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[2419.203564] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6/event5 (input)
UDEV  [2419.204762] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6/event5 (input)
KERNEL[2419.209363] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6 (input)
KERNEL[2419.209428] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0001/hidraw/hidraw0 (hidraw)
KERNEL[2419.209503] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0001 (hid)
KERNEL[2419.209551] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0 (usb)
UDEV  [2419.210558] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6 (input)
UDEV  [2419.211653] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0001/hidraw/hidraw0 (hidraw)
UDEV  [2419.211688] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0001 (hid)
UDEV  [2419.212557] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0 (usb)
KERNEL[2419.224334] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input7/mouse1 (input)
UDEV  [2419.224870] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input7/mouse1 (input)
KERNEL[2419.230202] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input7/event6 (input)
UDEV  [2419.230805] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input7/event6 (input)
KERNEL[2419.242421] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input7 (input)
KERNEL[2419.242471] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/usbmisc/hiddev0 (usbmisc)
KERNEL[2419.242494] remove   /class/usbmisc (class)
KERNEL[2419.243599] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0002/hidraw/hidraw1 (hidraw)
UDEV  [2419.243652] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input7 (input)
KERNEL[2419.243684] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0002 (hid)
UDEV  [2419.243711] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/usbmisc/hiddev0 (usbmisc)
KERNEL[2419.243731] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1 (usb)
UDEV  [2419.243744] remove   /class/usbmisc (class)
UDEV  [2419.243767] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0002/hidraw/hidraw1 (hidraw)
UDEV  [2419.244032] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0002 (hid)
UDEV  [2419.246158] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1 (usb)
KERNEL[2419.263617] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 (usb)
UDEV  [2419.264298] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 (usb)
KERNEL[2419.625470] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 (usb)
KERNEL[2419.625833] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0 (usb)
KERNEL[2419.628407] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0003 (hid)
KERNEL[2419.628573] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13 (input)
KERNEL[2419.628661] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13/event5 (input)
KERNEL[2419.628730] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0003/hidraw/hidraw0 (hidraw)
KERNEL[2419.628798] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1 (usb)
KERNEL[2419.634724] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0004 (hid)
KERNEL[2419.634975] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14 (input)
KERNEL[2419.635062] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14/mouse1 (input)
KERNEL[2419.635144] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14/event6 (input)
KERNEL[2419.635163] add      /class/usbmisc (class)
KERNEL[2419.635230] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/usbmisc/hiddev0 (usbmisc)
UDEV  [2419.635438] add      /class/usbmisc (class)
KERNEL[2419.635493] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0004/hidraw/hidraw1 (hidraw)
UDEV  [2419.639586] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 (usb)
UDEV  [2419.643208] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0 (usb)
UDEV  [2419.643328] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1 (usb)
UDEV  [2419.645231] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13 (input)
UDEV  [2419.645635] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0004 (hid)
UDEV  [2419.647765] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13/event5 (input)
UDEV  [2419.650340] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/0003:0E8F:00A5.0004/hidraw/hidraw1 (hidraw)
UDEV  [2419.656049] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14 (input)
UDEV  [2419.657513] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0003 (hid)
UDEV  [2419.658340] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/usbmisc/hiddev0 (usbmisc)
UDEV  [2419.660990] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14/event6 (input)
UDEV  [2419.666605] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14/mouse1 (input)
UDEV  [2419.666707] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/0003:0E8F:00A5.0003/hidraw/hidraw0 (hidraw)
KERNEL[2419.910780] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3 (usb)
KERNEL[2419.916258] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0 (usb)
KERNEL[2419.918092] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1 (usb)
UDEV  [2419.925342] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3 (usb)
UDEV  [2419.927455] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0 (usb)
UDEV  [2419.928843] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1 (usb)
```

Stay tuned for the HDD output ...

Thar she blows! From the HDD:

```
$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[74.861493] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3 (usb)
KERNEL[74.867141] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0 (usb)
KERNEL[74.869100] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1 (usb)
UDEV  [74.889421] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3 (usb)
KERNEL[74.908406] add      /module/rc_core (module)
KERNEL[74.908527] add      /class/rc (class)
UDEV  [74.909169] add      /module/rc_core (module)
UDEV  [74.909457] add      /class/rc (class)
KERNEL[74.923324] add      /module/dvb_core (module)
KERNEL[74.923430] add      /class/dvb (class)
UDEV  [74.923749] add      /module/dvb_core (module)
UDEV  [74.923776] add      /class/dvb (class)
KERNEL[74.943502] add      /module/dvb_usb_v2 (module)
UDEV  [74.943847] add      /module/dvb_usb_v2 (module)
KERNEL[74.951258] add      /module/rtl2830 (module)
UDEV  [74.951583] add      /module/rtl2830 (module)
KERNEL[74.954167] add      /module/dvb_usb_rtl28xxu (module)
UDEV  [74.954518] add      /module/dvb_usb_rtl28xxu (module)
KERNEL[75.016072] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/i2c-8 (i2c)
UDEV  [75.016702] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/i2c-8 (i2c)
KERNEL[75.016848] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.demux0 (dvb)
KERNEL[75.016939] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.dvr0 (dvb)
KERNEL[75.016971] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.net0 (dvb)
UDEV  [75.019106] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.dvr0 (dvb)
UDEV  [75.019142] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.demux0 (dvb)
UDEV  [75.019624] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.net0 (dvb)
KERNEL[75.055418] add      /module/rtl2832 (module)
UDEV  [75.055740] add      /module/rtl2832 (module)
KERNEL[75.058711] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.frontend0 (dvb)
UDEV  [75.059653] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/dvb/dvb0.frontend0 (dvb)
KERNEL[75.070943] add      /module/e4000 (module)
UDEV  [75.071209] add      /module/e4000 (module)
KERNEL[75.092501] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0 (rc)
KERNEL[75.092542] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/input14 (input)
KERNEL[75.092567] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/input14/event13 (input)
KERNEL[75.107677] add      /bus/usb/drivers/dvb_usb_rtl28xxu (drivers)
UDEV  [75.107820] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1 (usb)
UDEV  [75.108090] add      /bus/usb/drivers/dvb_usb_rtl28xxu (drivers)
UDEV  [75.108236] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0 (usb)
KERNEL[75.132199] add      /module/ir_jvc_decoder (module)
UDEV  [75.132229] add      /module/ir_sanyo_decoder (module)
KERNEL[75.132241] add      /module/ir_rc5_decoder (module)
UDEV  [75.132252] add      /module/ir_rc5_decoder (module)
KERNEL[75.132264] add      /module/ir_sanyo_decoder (module)
UDEV  [75.132276] add      /module/ir_jvc_decoder (module)
KERNEL[75.132498] add      /module/ir_rc6_decoder (module)
UDEV  [75.133182] add      /module/ir_rc6_decoder (module)
KERNEL[75.133787] add      /module/ir_sony_decoder (module)
UDEV  [75.134512] add      /module/ir_sony_decoder (module)
KERNEL[75.144604] add      /module/ir_mce_kbd_decoder (module)
KERNEL[75.144747] add      /devices/virtual/input/input15 (input)
KERNEL[75.144924] add      /devices/virtual/input/input15/mouse2 (input)
KERNEL[75.144970] add      /devices/virtual/input/input15/event14 (input)
UDEV  [75.145589] add      /devices/virtual/input/input15 (input)
KERNEL[75.146325] add      /module/ir_nec_decoder (module)
UDEV  [75.146650] add      /devices/virtual/input/input15/mouse2 (input)
UDEV  [75.146678] add      /devices/virtual/input/input15/event14 (input)
UDEV  [75.146691] add      /module/ir_nec_decoder (module)
UDEV  [75.146702] add      /module/ir_mce_kbd_decoder (module)
KERNEL[75.149065] add      /module/lirc_dev (module)
UDEV  [75.149448] add      /module/lirc_dev (module)
KERNEL[75.149602] add      /class/lirc (class)
UDEV  [75.150114] add      /class/lirc (class)
KERNEL[75.151963] add      /module/ir_lirc_codec (module)
UDEV  [75.152214] add      /module/ir_lirc_codec (module)
KERNEL[75.152950] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/lirc0 (lirc)
UDEV  [75.157024] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0 (rc)
UDEV  [75.157937] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/lirc0 (lirc)
UDEV  [75.158755] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/input14 (input)
UDEV  [75.162424] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/input14/event13 (input)


```

This appears twice in the HDD output, where the dongle works, and not at all in the SSD output:

```
KERNEL[74.954167] add      /module/dvb_usb_rtl28xxu (module)
UDEV  [74.954518] add      /module/dvb_usb_rtl28xxu (module)
```

The SSD output also has a lot of 'remove' entries, whereas the HDD output has none. 

Really odd. Maybe the two installs are not the identical twins I thought they were after all. I've been using this setup for a few weeks now and this is the only difference that has cropped up. Everything else is identical, except one's a lot faster. :-k

---

### Post by matt_symes on 2015-12-28
Hi BuckyBall,

udev is not seeing the TV dongle when the laptop is booted from the SSD drive. Those 'remove' entries are a surprise as well.

How did you create the clone ? Have you tried to recreate the clone ? 

This is what i would try first in case something went wrong with the clone.

Kind regards

---

### Post by Bucky Ball on 2015-12-28
Too much water under the bridge to cloning the HDD again, too many changes made from the original (and I really don't have time to faff about with anything that major as the uni research new year has started for me as a post-grad and already getting stuck into it ahead of time).

I used fsarchiver from memory. Have to check another thread but pretty sure that was it. The system was running at the time it was cloned and perhaps this is a consequence of that. Others have said not to do that since, but I saw no such advice when I was researching doing it. 

Nothing else seems different 'to the naked eye' or in computing experience, but who knows what's happening 'under the hood'. Issues may arise when I try and do specific things in future. :-k

---

### Post by matt_symes on 2015-12-29
Hi BuckyBall

> **Bucky Ball said:**
> Too much water under the bridge to cloning the HDD again, too many changes made from the original (and I really don't have time to faff about with anything that major as the uni research new year has started for me as a post-grad and already getting stuck into it ahead of time).

I used fsarchiver from memory. Have to check another thread but pretty sure that was it. The system was running at the time it was cloned and perhaps this is a consequence of that. Others have said not to do that since, but I saw no such advice when I was researching doing it. 

Nothing else seems different 'to the naked eye' or in computing experience, but who knows what's happening 'under the hood'. Issues may arise when I try and do specific things in future. :-k

I generally try to clone using ddrescue or some such and never on a live system where the files can change underneath me.

Anyway, the usual procedure when adding a hotplug device goes something like this (pretty simplified or I'll be typing a novel).

The device is plugged in.

The kernel recognises the new device, gets some information from the device such as vendor and product ID from which it constructs a MODALIAS line, and passes that as a uevent over the netlink socket into user space.

udev listens on the netlink socket for uevent events.

when it receives an add event event, it will create the device node under /dev and, using the MODALIAS string, will call modprobe to load the device driver associated with that MODALIAS string.

The udev rules can be used to modify the behaviour of udev when a device is added. 

The mapping between the modalias string and the module name is stored in the file

```
/lib/modules/$(uname -r)/modules.alias
```

You can load kernel modules using the modalias string passed to udev over the netlink socket.
```

matthew-xu-16-04:/home/matthew:7 % grep -m1 dvb_as102 /lib/modules/$(uname -r)/modules.alias
alias usb:v2137p0001d*dc*dsc*dp*ic*isc*ip*in* dvb_as102
matthew-xu-16-04:/home/matthew:7 % lsmod | grep dvb_as102
matthew-xu-16-04:/home/matthew:7 % sudo modprobe "usb:v2137p0001d*dc*dsc*dp*ic*isc*ip*in*"
[sudo] password for matthew: 
matthew-xu-16-04:/home/matthew:7 % lsmod | grep dvb_as102                                 
dvb_as102              28672  0
dvb_core              122880  1 dvb_as102
matthew-xu-16-04:/home/matthew:7 % sudo modprobe -r "usb:v2137p0001d*dc*dsc*dp*ic*isc*ip*in*"
matthew-xu-16-04:/home/matthew:7 % 
```

Somewhere in this merry dance it's failing on your system.

Do you have the time to see if we can track down where it's failing ? 

I know you're getting pretty busy so it's your call.

Kind regards

---

### Post by Bucky Ball on 2015-12-29
> **matt_symes said:**
> Do you have the time to see if we can track down where it's failing ? 

I know you're getting pretty busy so it's your call.

Kind regards

Thanks matt_symes. Appreciate the great explanation. Yes, I have time to dip in and dip out to try things, just can't afford two or three days with the computer out of action (and a possible question mark with when it will be in action) which could/probably will be the case with a re-clone. It took me three days to get things to a satisfactory resolution when I first cloned, but had put that time aside before the real business started (because I knew I wouldn't have time to do it once things got rolling). 

I didn't use the computer to do anything at all while the archive was being created, just walked away and left it, but won't be doing it from a running system again. Even though both appear the same to the naked eye, this has proved that they're not. 

Yep, just checked. I created the fsarchive from a running system, then restored that to the SSD [by the looks of this]("http://ubuntuforums.org/showthread.php?t=2306013").

---

### Post by Bucky Ball on 2015-12-29
I had a look here and:

```
alias usb:v15F4p0131d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD3AFd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD39Dd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD395d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0458p707Fd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpA803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0413p6A03d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD394d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v185Bp0620d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1104d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD393d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD3A8d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00D7d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1102d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00D3d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0413p6680d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1101d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpC803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00E0d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00B3d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpB803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00A9d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2832d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v14AAp0161d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v14AAp0160d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2831d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
```

I can make sense of and try things from the example you gave, but not sure which one of the entries from the file above I should:

```
sudo modprobe "usb:v2137p0001d*dc*dsc*dp*ic*isc*ip*in*"
```

For instance:

```
sudo modprobe "usb:v15F4p0131d*dc*dsc*dp*ic*isc*ip*in*"
```

... as I don't have the 'v2137' entry in your example. I'll boot into 12.04 LTS some time and see if that throws some light.

*** Hang on. From lsusb:

```
Bus 002 Device 004: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T
```

... matches this entry:

```
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
```

That would be the one to modprobe, if I'm assuming correctly ...

Better try it ...
_____

Result:

```
sudo modprobe "usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in*"
[sudo] password for plimple: 
modprobe: ERROR: ../libkmod/libkmod-module.c:180 kmod_module_parse_depline() ctx=0x7f81e5aa0010 path=/lib/modules/3.13.0-71-lowlatency/kernel/drivers/media/dvb-frontends/rtl2830.ko error=No such file or directory
modprobe: ERROR: could not insert 'dvb_usb_rtl28xxu': Unknown symbol in module, or unknown parameter (see dmesg)
```

I should add this:

```
grep -m1 dvb_as102 /lib/modules/$(uname -r)/modules.alias
alias usb:v2137p0001d*dc*dsc*dp*ic*isc*ip*in* dvb_as102
```

I get the same result as you there, even though that usb:v2137 is not in my file. :-k Probably obvious why and my lack of coding nous talking. :)

---

### Post by matt_symes on 2015-12-29
Hi BuckyBall,

When booting from the SSD, open a terminal and type

```
udevadm monitor -p | grep MODALIAS
```

Plug in the dvb dongle. You should get some modalias lines displayed similar the lines below.
```

matthew-xu-16-04:/home/matthew:0 % udevadm monitor -p | grep MODALIAS
MODALIAS=usb:v0718p0697d0100dc00dsc00dp00ic08isc06ip50in00
MODALIAS=usb:v0718p0697d0100dc00dsc00dp00ic08isc06ip50in00
MODALIAS=scsi:t-0x00
MODALIAS=scsi:t-0x00
```

The MODALIAS lines are what the kernel constructs from the information it gets from the device and is what udev uses to load the correct modules.

If there are no modalias lines then the kernel is at fault. If there are then the problem is most probably udev.

Also, is udev creating a device node for the dvb stick in /dev ?

You can check quickly using inotify-tools

```
sudo apt-get install inotify-tools
```

```
inotifywait -m /dev -e create
```

... then plug the dongle in.

Expect to see output like this below. I created a temporary file called /dev/tmp.node

```

matthew-xu-16-04:/home/matthew:0 % inotifywait -m /dev -e create
Setting up watches.
Watches established.
/dev/ CREATE tmp.node
```

**EDIT:**

Can you also post the output of

```
uname -a
```

BTW: I'll have a good look at the end of your last post after i have eaten as those errors are interesting and may point towards the problem !

(From your last post)

```
sudo modprobe "usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in*"
[sudo] password for plimple: 
modprobe: ERROR: ../libkmod/libkmod-module.c:180 kmod_module_parse_depline() ctx=0x7f81e5aa0010 path=/lib/modules/3.13.0-71-lowlatency/kernel/drivers/media/dvb-frontends/rtl2830.ko error=No such file or directory
modprobe: ERROR: could not insert 'dvb_usb_rtl28xxu': Unknown symbol in module, or unknown parameter (see dmesg)
```

I'll post a bit more later :) Just try to do too many things at once at the moment.

Kind regards

---

### Post by Bucky Ball on 2015-12-29
Okay, thanks again. For 'udevadm monitor -p | grep MODALIAS' I get nothing when I plug the dongle in, but I get this when I unplug it, if it is of any use:

```

$ udevadm monitor -p | grep MODALIAS
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
```

After installing inotify-tools, 'inotifywait -m /dev -e create' give me nothing. No output at all. 'uname -a' gives:

```
Linux TrustMini 3.13.0-71-lowlatency #114-Ubuntu SMP PREEMPT Tue Dec 1 03:30:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by matt_symes on 2015-12-30
Hi BuckyBall,

> **Bucky Ball said:**
> Okay, thanks again. For 'udevadm monitor -p | grep MODALIAS' I get nothing when I plug the dongle in, but I get this when I unplug it, if it is of any use:

```

$ udevadm monitor -p | grep MODALIAS
MODALIAS=usb:**v0BDAp2838d**0100dc00dsc00dp00icFFiscFFipFFin00
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01
MODALIAS=usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
```


Well that's just odd if you're getting those MODALIAS lines when you *remove* the stick !

That MODALIAS line looks to be referencing the correct driver. 

A grep on the bold text above shows it's the correct MODALIAS line for the driver but the kernel should be emitting it when when the device is plugged in and not when it's removed. 

```

matthew-xu-16-04:/home/matthew/temp:2 % grep "usb:v0BDAp2838" /mnt/old_root/lib/modules/3.16.0-57-generic/modules.alias
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* **dvb_usb_rtl28xxu**
matthew-xu-16-04:/home/matthew/temp:2 %
```

3.16 is the oldest kernel i have but i'm sure you'll see it if you run the command below on your kernel's modules.alias file so the modalias line looks correct for the hardware.

> After installing inotify-tools, 'inotifywait -m /dev -e create' give me nothing. No output at all.

That's really unusual as well. When you cloned the drive was the DVB stick plugged into your PC at the time ?

When the device is *not* plugged in, can you run this command. Just copy and paste it into the terminal. 

Does it return any output,  besides 'permission denied' on the debug directory ?

```
find /sys -name "modalias" -exec grep "usb:v0BDAp2838" '{}' \;
```

>  'uname -a' gives:

```
Linux TrustMini 3.13.0-71-lowlatency #114-Ubuntu SMP PREEMPT Tue Dec 1 03:30:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

I would suggest either booting into an older kernel and/or installing a new kernel and see if you get the same issue.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It looks to be something hinkey with the kernel maybe. This one's odd.

Kind regards

---

### Post by Bucky Ball on 2016-01-07
This is what I'm getting from 'dmesg' on the HDD install, where the dongle works:

```
[   52.682388] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[   52.782440] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=2838
[   52.782446] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   52.782449] usb 2-1.3: Product: RTL2838UHIDIR
[   52.782452] usb 2-1.3: Manufacturer: Realtek
[   52.788226] usb 2-1.3: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[   52.851371] usb 2-1.3: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   52.851399] DVB: registering new adapter (Realtek RTL2832U reference design)
[   52.854699] usb 2-1.3: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[   52.864542] i2c i2c-0: e4000: Elonics E4000 successfully identified
[   52.876297] Registered IR keymap rc-empty
[   52.876462] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc1/input16
[   52.876665] rc1: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc1
[   52.876936] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input17
[   52.877193] rc rc1: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[   52.877199] usb 2-1.3: dvb_usb_v2: schedule remote query interval to 400 msecs
[   52.889799] usb 2-1.3: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
```

This is what I get from the SSD install, where the dongle doesn't work:

```
[   24.667838] usb 2-1.3: new high-speed USB device number 4 using ehci-pci
[   24.770477] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=2838
[   24.770483] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   24.770486] usb 2-1.3: Product: RTL2838UHIDIR
[   24.770489] usb 2-1.3: Manufacturer: Realtek
[  192.847271] usb 2-1.3: USB disconnect, device number 4
[  196.883881] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[  196.986638] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=2838
[  196.986644] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  196.986647] usb 2-1.3: Product: RTL2838UHIDIR
[  196.986650] usb 2-1.3: Manufacturer: Realtek
```

Here's the ouput from 'nano /lib/modules/$(uname -r)/modules.alias' on the HDD:

```
alias usb:v15F4p0131d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD3AFd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD39Dd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD395d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0458p707Fd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpA803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0413p6A03d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD394d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v185Bp0620d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1104d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD393d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD3A8d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00D7d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1102d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00D3d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0413p6680d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1101d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpC803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00E0d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00B3d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpB803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00A9d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2832d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v14AAp0161d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v14AAp0160d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2831d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
```

The SSD:

```
alias usb:v15F4p0131d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD3AFd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD39Dd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD395d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0458p707Fd*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpA803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0413p6A03d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD394d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v185Bp0620d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1104d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD393d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1B80pD3A8d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00D7d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1102d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00D3d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0413p6680d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1D19p1101d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpC803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00E0d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00B3d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v1F4DpB803d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0CCDp00A9d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2832d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v14AAp0161d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v14AAp0160d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
alias usb:v0BDAp2831d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
```

'find /sys -name "modalias" -exec grep "usb:v0BDAp2838" '{}' \;' on the HDD install gives me:

```
usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01

```
SSD:

```
usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin00
usb:v0BDAp2838d0100dc00dsc00dp00icFFiscFFipFFin01

```

There's gotta be a blockage somewhere but a quick scan gives no clues ... dashing off but back later ...

---

### Post by Bucky Ball on 2016-01-07
The HDD output from your command. The SSD gives no output from this command. 

```
$ grep "usb:v0BDAp2838" /mnt/2013BUP1/lib/modules/3.13.0-71-lowlatency/modules.alias
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
```

In fact, dvb_usb_rtl28xxu doesn't seem to be on the SSD install anywhere it should be according to some of the things I've read. I can't find it anywhere. I also have no /dev/dvb. All missing on this install. Truly puzzled. :-k

---

### Post by matt_symes on 2016-01-08
Hi

> **Bucky Ball said:**
> The HDD output from your command. The SSD gives no output from this command. 

```
$ grep "usb:v0BDAp2838" /mnt/2013BUP1/lib/modules/3.13.0-71-lowlatency/modules.alias
alias usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*in* dvb_usb_rtl28xxu
```

In fact, dvb_usb_rtl28xxu doesn't seem to be on the SSD install anywhere it should be according to some of the things I've read. I can't find it anywhere. I also have no /dev/dvb. All missing on this install. Truly puzzled. :-k

If there's no driver or modules.alias entry for the dongle then that'll explain why udev is not doing its thing :)

Does the driver exist at all on the SSD ? 

If you're still mounting at /mnt/2013BUP1/ for the SSD, then what does this return ? Copy and paste as usual :)

```
find /mnt/2013BUP1/lib/modules/3.13.0-71-lowlatency -iname "*dvb-usb-rtl28xxu*"
```

If it finds the module then we can recreate the modules.alias file in case there's a problem there and it's got corrupted somehow.

I think the command is depmod and you'll have to run it in a standard chroot for the SSD's root partition, unless you boot directly into the SSD's install. 

I would need to double check the command though.

Kind regards

---

### Post by Bucky Ball on 2016-01-08
```
find /lib/modules/3.13.0-71-lowlatency -iname "*dvb-usb-rtl28xxu*"
```

... when booted to the SSD install outputs nothing. Weird.

---

### Post by matt_symes on 2016-01-08
Hi BuckyBall

> **Bucky Ball said:**
> ```
find /lib/modules/3.13.0-71-lowlatency -iname "*dvb-usb-rtl28xxu*"
```

... when booted to the SSD install outputs nothing. Weird.

Well that's the problem then. 

The low-latency kernel definitely contains that kernel module ? I use generic so i don't have much exposure to the low-latency kernel.

As a sanity check, run the same command from your spinning rust install . It should find the module. BTW: Are you using the same kernel on the spinning rust ?

It's definitely included with the *-generic* kernels. Here's mine.

```

matthew-xu-16-04:/lib/udev/rules.d:5 % find /lib/modules/$(uname -r) -iname "*dvb-usb-rtl28xxu*"
/lib/modules/4.4.0-040400rc7-generic/kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-rtl28xxu.ko
matthew-xu-16-04:/lib/udev/rules.d:5 % 
```

I'm beginning to think we should reinstall the kernel but i want to know why the kernel module is missing.

Obviously something went seriously wrong with your cloning. Permissions maybe ? Missed directories maybe ?

I'm pretty sure we have identified the problem though :)

Anyway, I'm off out in 20 mins.

Kind regards

---

### Post by Bucky Ball on 2016-01-08
From the hard drive install where it works:

```
$ find /lib/modules/3.13.0-71-lowlatency -iname "*dvb-usb-rtl28xxu*"
/lib/modules/3.13.0-71-lowlatency/kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-rtl28xxu.ko
```

Using kernel 3.13.0-71-lowlatency, same one I'm using on the SSD install. I tried the generic kernel there too. No different. Dongle works on all kernels on the HDD install (yep, aware the driver is in the kernel by default as I had been anticipating this since 12.04 LTS where you needed to jump through some hoops to get it to work).

Reinstalling the kernel module is what I've been trying to figure out how to do most recently on this ...

---

### Post by matt_symes on 2016-01-08
Hi

> **Bucky Ball said:**
> Using kernel 3.13.0-71-lowlatency, same one I'm using on the SSD install. I tried the generic kernel there too. No different. Dongle works on all kernels on the HDD install (yep, aware the driver is in the kernel by default as I had been anticipating this since 12.04 LTS where you needed to jump through some hoops to get it to work).


That is odd. Is that kernel module anywhere on the ssd drive ?

What are the permissions on that directory o the ssd as well ?

```
ls -l /lib/modules/$(uname -r)/kernel/drivers/media/usb/dvb-usb-v2/
```

> Reinstalling the kernel module is what I've been trying to figure out how to do most recently on this ...

I would try to reinstall the entire kernel. This may work.

```
sudo apt-get install --reinstall linux-image-3.13.0-71-lowlatency
```

I've never tried that command on a running kernel so you may want to boot into another one.

Kind regards

---

### Post by Bucky Ball on 2016-01-08
```
$ ls -l /lib/modules/$(uname -r)/kernel/drivers/media/usb/dvb-usb-v2/
ls: cannot access /lib/modules/3.13.0-71-lowlatency/kernel/drivers/media/usb/dvb-usb-v2/: No such file or directory
```

I'll boot into another kernel and run the update kernel command. Something else odd. I found a page explaining how to reinstall the kernel via Synaptic. All good. But when I looked in there, the -74 kernel is installed ... somewhere. The odd part is that I am only being offered up to the -71 kernel when I boot the machine. That's it. No -72 or 73. I haven't updated/upgraded the HDD install for awhile so don't think it has anything to do with that, but will recheck.

In the meantime, wish me luck reinstalling the kernel.

---

### Post by Bucky Ball on 2016-01-08
Bingo. Either would have worked, your command or Synaptics, but I was on my way to Synaptics in the -70 kernel. Reinstalled the lowlatency -71 kernel and here's the relevant dmesg output:

```
[   46.004707] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[   46.102285] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=2838
[   46.102291] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   46.102294] usb 2-1.3: Product: RTL2838UHIDIR
[   46.102296] usb 2-1.3: Manufacturer: Realtek
[   46.139818] usb 2-1.3: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[   46.201052] usb 2-1.3: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   46.201070] DVB: registering new adapter (Realtek RTL2832U reference design)
[   46.213961] usb 2-1.3: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[   46.227707] i2c i2c-8: e4000: Elonics E4000 successfully identified
[   46.238843] Registered IR keymap rc-empty
[   46.238950] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0/input16
[   46.239025] rc0: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc0
[   46.244853] IR NEC protocol handler initialized
[   46.245231] IR RC6 protocol handler initialized
[   46.247439] IR JVC protocol handler initialized
[   46.248109] IR RC5(x) protocol handler initialized
[   46.248181] usb 2-1.3: dvb_usb_v2: schedule remote query interval to 400 msecs
[   46.250968] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input17
[   46.251866] IR MCE Keyboard/mouse protocol handler initialized
[   46.252102] lirc_dev: IR Remote Control driver registered, major 250 
[   46.253635] IR SANYO protocol handler initialized
[   46.257685] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[   46.257694] IR LIRC bridge handler initialized
[   46.258859] IR Sony protocol handler initialized
[   46.270806] usb 2-1.3: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
[   46.270894] usbcore: registered new interface driver dvb_usb_rtl28xxu
```

Me-TV works without issue (no need to scan as guess the .me-tv config files is in /home as in the HDD install) and all is good with the world. 

Thanks tons matt_symes for sticking with me on this and the input. :)

We've solved this but in doing so have shown there is something a little 'Frankenstein's clone' about this SSD install. I'm bemused as to why I see the lowlatency and generic -74 kernels installed, according to Synaptic, but not as options when I boot the machine, nor when I 'sudo update-grub'. Will dig around there and perhaps post a new thread. 

Thanks again.

* Further note, though. I was a bit worried that on the next kernel upgrade this would break again, but I did manage to get my SSD install to upgrade to the 3.13.0-74-lowlatency kernel: by updating/upgrading the HDD install! Not sure how that works, but I'd tried updating/upgrading the SSD install but wouldn't offer the 74 kernel. HDD was at the 3.13.0-71-lowlatency kernel so booted into that, update/upgrade, reboot, SSD boot offers me the 3.13.0-74-lowlatency kernel! 

Oh, well. The wifi dongle still works fine as does everything else, but really no idea about the kernel upgrade. This install is a long story (and I was thinking it would take an hour or two when I first set out on this quest). :D

---

### Post by matt_symes on 2016-01-08
Hi

That's something really odd that went on with your kernels there Bucky Ball. 

We took the long way round to find the problem but it was an odd problem so that's no real surprise. 

I'm glad it's sorted :)

Kind regards

---

### Post by Bucky Ball on 2016-01-08
I think I figured out the kernel thing whilst doing my 'morning meditations' (if you know what I mean). As the install on HDD is controlling the grub, naturally, that need an 'update-grub' to pick up any new kernels in any of my other installs, including the SSD install. At least I think that's what's happening. Nothing unusual there. 

Tnx again. :)

---

