---
title: "Displaylink udl in xubuntu 13.10"
date: 2014-03-13
forum: Hardware
---

### Post by mscho1997 on 2014-03-13
Also asked in askubuntu, but as there wasn't any reply, I'd like to ask ubuntu forums also. Thank you.
[http://askubuntu.com/questions/433525/displaylink-udl-in-xubuntu-13-10](http://askubuntu.com/questions/433525/displaylink-udl-in-xubuntu-13-10)

          I'm using Xubuntu Saucy Salamander (13.10).
  I'm trying to connect displaylink wireless monitor with my linux machine.
  My configuration is
  Nvidia GT310M
Intel HD Graphics for 1st gen i5 processors
[with Optimus graphics - bumblebee]
  And uname -r is
  3.11.0-12-generic
  And dmesg provides me
  [  580.150091] usb 2-1.2: new high-speed USB device number 6 using ehci-pci
[  580.243210] usb 2-1.2: New USB device found, idVendor=17e9, idProduct=4047
[  580.243216] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  580.243219] usb 2-1.2: Product: WUSB Audio/Video Device
[  580.243222] usb 2-1.2: Manufacturer: Alereon
[  580.243225] usb 2-1.2: SerialNumber: 00000000-00030C
[  580.245689] [drm] vendor descriptor length:e0 data:00 00 00 00 00 00 00 00 00 00 00
[  580.245694] [drm:udl_parse_vendor_descriptor] *ERROR* Unrecognized vendor firmware descriptor
[  580.584559] Raw EDID:
[  580.584567]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584569]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584572]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584574]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584576]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584578]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584581]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584583]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  580.584588] udl 2-1.2:1.0: DVI-I-1: EDID invalid.
[  580.585584] udl 2-1.2:1.0: fb1: udldrmfb frame buffer device
[  580.585592] [drm] Initialized udl 0.0.1 20120220 on minor 1
[  580.707775] usbcore: registered new interface driver snd-usb-audio
  And lsmod | grep udl gives me
  udl                    24626  0 
drm_usb                13134  1 udl
syscopyarea            12529  1 udl
sysfillrect            12701  1 udl
sysimgblt              12640  1 udl
drm_kms_helper         52651  2 udl,i915
drm                   296739  5 udl,i915,drm_usb,drm_kms_helper
  However, xrandr --listproviders only gives me
  Providers: number : 1
Provider 0: id: 0x47 cap: 0xb, Source Output, Sink Output, Sink Offload crtcs: 3 outputs: 5 associated providers: 0 name:Intel
  Also, only 1 framebuffer (fb0 for Intel) is registered.
  How can I work this problem out? Thank you
  P.S. The device is based on DL-125 chip.

---

