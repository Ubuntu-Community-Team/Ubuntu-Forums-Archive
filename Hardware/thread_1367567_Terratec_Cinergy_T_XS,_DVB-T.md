---
title: "Terratec Cinergy T XS, DVB-T"
date: 2009-12-29
forum: Hardware
---

### Post by buggybugg on 2009-12-29
I read somewhere that this stick is recognized "plug & play", you just have to download the firmware. I did this with the following commands:

```
wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip

unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

wget http://linuxtv.org/hg/v4l-dvb/raw-file/6bab82c6096e/linux/Documentation/video4linux/extract_xc3028.pl

sudo chmod a+x extract_xc3028.pl
sudo ./extract_xc3028.pl

sudo cp xc3028-v27.fw /lib/firmware
```When I plug in the stick messages log shows this. The Card doesnt work with Kaffeine or Me TV. There is no /dev/dvb (I think there should be..)

The messages log shows this.
```
Dec 29 22:40:27 acer-laptop kernel: [ 2527.165104] usb 1-3: new high speed USB device using ehci_hcd and address 4
Dec 29 22:40:27 acer-laptop kernel: [ 2527.305410] usb 1-3: configuration #1 chosen from 1 choice
Dec 29 22:40:27 acer-laptop kernel: [ 2527.306649] em28xx: New device TerraTec Electronic GmbH Cinergy T USB XS @ 480 Mbps (0ccd:0043, interface 0, class 0)
Dec 29 22:40:27 acer-laptop kernel: [ 2527.306821] em28xx #0: chip ID is em2870
Dec 29 22:40:27 acer-laptop kernel: [ 2527.442854] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 43 00 c0 12 81 00 6a 24 8e 34
Dec 29 22:40:27 acer-laptop kernel: [ 2527.442883] em28xx #0: i2c eeprom 10: 00 00 06 57 02 0c 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.442909] em28xx #0: i2c eeprom 20: 44 00 00 00 f0 10 01 00 00 00 00 00 5b 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.442933] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 59 54 dc 48
Dec 29 22:40:27 acer-laptop kernel: [ 2527.442957] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.442980] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443003] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 43 00 69 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443027] em28xx #0: i2c eeprom 70: 6e 00 65 00 72 00 67 00 79 00 20 00 54 00 20 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443051] em28xx #0: i2c eeprom 80: 55 00 53 00 42 00 20 00 58 00 53 00 00 00 34 03
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443076] em28xx #0: i2c eeprom 90: 54 00 65 00 72 00 72 00 61 00 54 00 65 00 63 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443099] em28xx #0: i2c eeprom a0: 20 00 45 00 6c 00 65 00 63 00 74 00 72 00 6f 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443123] em28xx #0: i2c eeprom b0: 6e 00 69 00 63 00 20 00 47 00 6d 00 62 00 48 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443147] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443172] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443196] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443219] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443248] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x31d7fede
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443254] em28xx #0: EEPROM info:
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443258] em28xx #0:    No audio on board.
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443263] em28xx #0:    500mA max power
Dec 29 22:40:27 acer-laptop kernel: [ 2527.443269] em28xx #0:    Table at 0x06, strings=0x246a, 0x348e, 0x0000
Dec 29 22:40:27 acer-laptop kernel: [ 2527.444102] em28xx #0: Identified as Terratec Cinergy T XS (card=43)
Dec 29 22:40:27 acer-laptop kernel: [ 2527.459689] Chip ID is not zero. It is not a TEA5767
Dec 29 22:40:27 acer-laptop kernel: [ 2527.459935] tuner 1-0060: chip found @ 0xc0 (em28xx #0)
Dec 29 22:40:27 acer-laptop kernel: [ 2527.460166] xc2028 1-0060: creating new instance
Dec 29 22:40:27 acer-laptop kernel: [ 2527.460173] xc2028 1-0060: type set to XCeive xc2028/xc3028 tuner
Dec 29 22:40:27 acer-laptop kernel: [ 2527.460191] usb 1-3: firmware: requesting xc3028-v27.fw
Dec 29 22:40:27 acer-laptop kernel: [ 2527.470352] xc2028 1-0060: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Dec 29 22:40:27 acer-laptop kernel: [ 2527.521068] xc2028 1-0060: Loading firmware for type=BASE (1), id 0000000000000000.
Dec 29 22:40:28 acer-laptop kernel: [ 2528.538910] xc2028 1-0060: Loading firmware for type=(0), id 000000000000b700.
Dec 29 22:40:28 acer-laptop kernel: [ 2528.555004] SCODE (20000000), id 000000000000b700:
Dec 29 22:40:28 acer-laptop kernel: [ 2528.555021] xc2028 1-0060: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Dec 29 22:40:28 acer-laptop kernel: [ 2528.689060] xc2028 1-0060: Loading firmware for type=BASE (1), id 0000000000000000.
Dec 29 22:40:29 acer-laptop kernel: [ 2529.683164] xc2028 1-0060: Loading firmware for type=(0), id 000000000000b700.
Dec 29 22:40:29 acer-laptop kernel: [ 2529.697904] SCODE (20000000), id 000000000000b700:
Dec 29 22:40:29 acer-laptop kernel: [ 2529.697921] xc2028 1-0060: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Dec 29 22:40:29 acer-laptop kernel: [ 2529.885072] em28xx #0: v4l2 driver version 0.1.2
Dec 29 22:40:29 acer-laptop kernel: [ 2529.890759] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
Dec 29 23:11:14 acer-laptop kernel: [ 4374.283771] usb 1-3: USB disconnect, address 4
Dec 29 23:11:14 acer-laptop kernel: [ 4374.283972] em28xx #0: disconnecting em28xx #0 video
Dec 29 23:11:14 acer-laptop kernel: [ 4374.283982] em28xx #0: V4L2 device /dev/vbi0 deregistered
Dec 29 23:11:14 acer-laptop kernel: [ 4374.284145] em28xx #0: V4L2 device /dev/video0 deregistered
Dec 29 23:11:14 acer-laptop kernel: [ 4374.284309] xc2028 1-0060: destroying instance
Dec 29 23:11:16 acer-laptop kernel: [ 4376.436094] usb 1-3: new high speed USB device using ehci_hcd and address 5
Dec 29 23:11:16 acer-laptop kernel: [ 4376.576456] usb 1-3: configuration #1 chosen from 1 choice
Dec 29 23:11:16 acer-laptop kernel: [ 4376.578100] em28xx: New device TerraTec Electronic GmbH Cinergy T USB XS @ 480 Mbps (0ccd:0043, interface 0, class 0)
Dec 29 23:11:16 acer-laptop kernel: [ 4376.578257] em28xx #0: chip ID is em2870
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708273] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 43 00 c0 12 81 00 6a 24 8e 34
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708303] em28xx #0: i2c eeprom 10: 00 00 06 57 02 0c 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708328] em28xx #0: i2c eeprom 20: 44 00 00 00 f0 10 01 00 00 00 00 00 5b 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708352] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 59 54 dc 48
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708377] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708400] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708423] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 43 00 69 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708448] em28xx #0: i2c eeprom 70: 6e 00 65 00 72 00 67 00 79 00 20 00 54 00 20 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708472] em28xx #0: i2c eeprom 80: 55 00 53 00 42 00 20 00 58 00 53 00 00 00 34 03
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708496] em28xx #0: i2c eeprom 90: 54 00 65 00 72 00 72 00 61 00 54 00 65 00 63 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708521] em28xx #0: i2c eeprom a0: 20 00 45 00 6c 00 65 00 63 00 74 00 72 00 6f 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708544] em28xx #0: i2c eeprom b0: 6e 00 69 00 63 00 20 00 47 00 6d 00 62 00 48 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708568] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708591] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708615] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708638] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708667] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x31d7fede
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708672] em28xx #0: EEPROM info:
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708678] em28xx #0:    No audio on board.
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708682] em28xx #0:    500mA max power
Dec 29 23:11:16 acer-laptop kernel: [ 4376.708689] em28xx #0:    Table at 0x06, strings=0x246a, 0x348e, 0x0000
Dec 29 23:11:16 acer-laptop kernel: [ 4376.717388] em28xx #0: Identified as Terratec Cinergy T XS (card=43)
Dec 29 23:11:16 acer-laptop kernel: [ 4376.728945] Chip ID is not zero. It is not a TEA5767
Dec 29 23:11:16 acer-laptop kernel: [ 4376.729226] tuner 1-0060: chip found @ 0xc0 (em28xx #0)
Dec 29 23:11:16 acer-laptop kernel: [ 4376.729448] xc2028 1-0060: creating new instance
Dec 29 23:11:16 acer-laptop kernel: [ 4376.729455] xc2028 1-0060: type set to XCeive xc2028/xc3028 tuner
Dec 29 23:11:16 acer-laptop kernel: [ 4376.729473] usb 1-3: firmware: requesting xc3028-v27.fw
Dec 29 23:11:16 acer-laptop kernel: [ 4376.739833] xc2028 1-0060: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Dec 29 23:11:16 acer-laptop kernel: [ 4376.789071] xc2028 1-0060: Loading firmware for type=BASE (1), id 0000000000000000.
Dec 29 23:11:17 acer-laptop kernel: [ 4377.743036] xc2028 1-0060: Loading firmware for type=(0), id 000000000000b700.
Dec 29 23:11:17 acer-laptop kernel: [ 4377.757901] SCODE (20000000), id 000000000000b700:
Dec 29 23:11:17 acer-laptop kernel: [ 4377.757912] xc2028 1-0060: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Dec 29 23:11:17 acer-laptop kernel: [ 4377.892069] xc2028 1-0060: Loading firmware for type=BASE (1), id 0000000000000000.
Dec 29 23:11:18 acer-laptop kernel: [ 4378.853062] xc2028 1-0060: Loading firmware for type=(0), id 000000000000b700.
Dec 29 23:11:18 acer-laptop kernel: [ 4378.868052] SCODE (20000000), id 000000000000b700:
Dec 29 23:11:18 acer-laptop kernel: [ 4378.868063] xc2028 1-0060: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Dec 29 23:11:19 acer-laptop kernel: [ 4379.053082] em28xx #0: v4l2 driver version 0.1.2
Dec 29 23:11:19 acer-laptop kernel: [ 4379.061784] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
```Please can you give me a hint what I did wrong???

---

