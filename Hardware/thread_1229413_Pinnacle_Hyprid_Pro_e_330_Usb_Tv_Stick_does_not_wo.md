---
title: "Pinnacle Hyprid Pro e 330 Usb Tv Stick does not work"
date: 2009-08-02
forum: Hardware
---

### Post by hiptrop on 2009-08-02
Hello and thanks for reading  !

I have some troubles with my usb tv stick and i just cannot solve it myself. i hope you can help me out. it seems to me, that the usb stick is recognised correctly .. but me-tv gives me an error... it cannot find the stick ! 

dmesg: 

```

[ 6440.036104] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 6440.176471] usb 1-3: configuration #1 chosen from 1 choice
[ 6441.034740] Linux video capture interface: v2.00
[ 6441.091186] em28xx v4l2 driver version 0.1.0 loaded
[ 6441.091248] em28xx new video device (2304:0226): interface 0, class 255
[ 6441.091257] em28xx Doesn't have usb audio class
[ 6441.091261] em28xx #0: Alternate settings: 8
[ 6441.091266] em28xx #0: Alternate setting 0, max size= 0
[ 6441.091271] em28xx #0: Alternate setting 1, max size= 0
[ 6441.091276] em28xx #0: Alternate setting 2, max size= 1448
[ 6441.091282] em28xx #0: Alternate setting 3, max size= 2048
[ 6441.091287] em28xx #0: Alternate setting 4, max size= 2304
[ 6441.091292] em28xx #0: Alternate setting 5, max size= 2580
[ 6441.091298] em28xx #0: Alternate setting 6, max size= 2892
[ 6441.091303] em28xx #0: Alternate setting 7, max size= 3072
[ 6441.091543] em28xx #0: chip ID is em2882/em2883
[ 6441.277178] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 26 02 d0 12 5c 03 8e 16 a4 1c
[ 6441.277204] em28xx #0: i2c eeprom 10: 6a 24 27 57 46 07 01 00 00 00 00 00 00 00 00 00
[ 6441.277227] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b e0 00 00
[ 6441.277250] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[ 6441.277273] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6441.277295] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6441.277317] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 50 00 69 00
[ 6441.277340] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
[ 6441.277363] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 00 00 16 03
[ 6441.277385] em28xx #0: i2c eeprom 90: 50 00 43 00 54 00 56 00 20 00 33 00 33 00 30 00
[ 6441.277408] em28xx #0: i2c eeprom a0: 65 00 00 00 1c 03 30 00 38 00 30 00 31 00 30 00
[ 6441.277431] em28xx #0: i2c eeprom b0: 31 00 32 00 30 00 37 00 34 00 30 00 30 00 00 00
[ 6441.277453] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6441.277476] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6441.277498] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6441.277521] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6441.277545] EEPROM ID= 0x9567eb1a, hash = 0x21b3a8bf
[ 6441.277549] Vendor/Product ID= 2304:0226
[ 6441.277553] AC97 audio (5 sample rates)
[ 6441.277556] 500mA max power
[ 6441.277560] Table at 0x27, strings=0x168e, 0x1ca4, 0x246a
[ 6441.277564] em28xx #0: 
[ 6441.277566] 
[ 6441.277570] em28xx #0: The support for this board weren't valid yet.
[ 6441.277575] em28xx #0: Please send a report of having this working
[ 6441.277579] em28xx #0: not to V4L mailing list (and/or to other addresses)
[ 6441.277582] 
[ 6441.317321] tuner' 3-0061: chip found @ 0xc2 (em28xx #0)
[ 6441.380834] xc2028 3-0061: creating new instance
[ 6441.380840] xc2028 3-0061: type set to XCeive xc2028/xc3028 tuner
[ 6441.380855] i2c-adapter i2c-3: firmware: requesting xc3028-v27.fw
[ 6441.481933] xc2028 3-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[ 6441.540099] xc2028 3-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[ 6442.469809] xc2028 3-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[ 6442.485196] xc2028 3-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
[ 6442.761564] tvp5150 3-005c: tvp5150am1 detected.
[ 6442.905364] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 6442.905372] em28xx #0: Found Pinnacle Hybrid Pro (2)
[ 6442.905414] usbcore: registered new interface driver em28xx
[ 6443.037207] em28xx-audio.c: probing for em28x1 non standard usbaudio
[ 6443.037214] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[ 6443.037792] Em28xx: Initialized (Em28xx Audio Extension) extension
[ 6443.233564] tvp5150 3-005c: tvp5150am1 detected.

```

if you need more information please tell me ! 

i use ubuntu 9.04 with all new updates installed ... 

thanks alot !

---

