---
title: "Pinnacle USB DVB Hybrid Pro"
date: 2010-01-31
forum: Hardware
---

### Post by Zec on 2010-01-31
Anyone got this item to work?
I was using this DVB-T stick with Ubuntu 9.04 and MRechbergers Drivers. Because of the Drivers are not longer adjusted to actual kernels, I'm trying to get it running with kernel-included drivers from V4L.

The stick is successfully detected and a device-file is created. At the moment, I'm testing with Ubuntu 10.04 alpha2 because the Bug 

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/278656](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/278656)

is already solved there (correct firmware for this stick is included now).

My dmesg-output is as follows:

em28xx: New device USB 2881 Video @ 480 Mbps (eb1a:2881, interface 0, class 0)
[   18.878017] em28xx #0: chip ID is em2882/em2883
[   18.903247] EXT3 FS on sda3, internal journal
[   18.903257] EXT3-fs: mounted filesystem with ordered data mode.
[   18.914216] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.914256] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.959270] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 81 28 58 12 5c 00 6a 20 6a 00
[   18.959282] em28xx #0: i2c eeprom 10: 00 00 04 57 64 57 00 00 60 f4 00 00 02 02 00 00
[   18.959292] em28xx #0: i2c eeprom 20: 56 00 01 00 00 00 02 00 b8 00 00 00 5b 1e 00 00
[   18.959302] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 02 00 00 00 00 00 00
[   18.959311] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959321] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959330] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 20 03 55 00 53 00
[   18.959340] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 38 00 31 00 20 00 56 00
[   18.959349] em28xx #0: i2c eeprom 80: 69 00 64 00 65 00 6f 00 00 00 00 00 00 00 00 00
[   18.959359] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959368] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959377] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959387] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959396] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959406] em28xx #0: i2c eeprom e0: 5a 00 55 aa 79 55 54 03 00 17 98 01 00 00 00 00
[   18.959415] em28xx #0: i2c eeprom f0: 0c 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00
[   18.959427] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xb8846b20
[   18.959429] em28xx #0: EEPROM info:
[   18.959430] em28xx #0:    AC97 audio (5 sample rates)
[   18.959432] em28xx #0:    USB Remote wakeup capable
[   18.959434] em28xx #0:    500mA max power
[   18.959436] em28xx #0:    Table at 0x04, strings=0x206a, 0x006a, 0x0000
[   18.960770] em28xx #0: Identified as Unknown EM2750/28xx video grabber (card=1)
[   18.960773] em28xx #0: Your board has no unique USB ID.
[   18.960776] em28xx #0: A hint were successfully done, based on eeprom hash.
[   18.960778] em28xx #0: This method is not 100% failproof.
[   18.960780] em28xx #0: If the board were missdetected, please email this log to:
[   18.960782] em28xx #0:     V4L Mailing List  <linux-media@vger.kernel.org>
[   18.960785] em28xx #0: Board detected as Pinnacle Hybrid Pro
[   19.020230] hda_codec: ALC268: BIOS auto-probing.
[   19.020909] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   19.069188] tvp5150 2-005c: chip found @ 0xb8 (em28xx #0)
[   19.133623] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.135763] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.136688] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.137429] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.138351] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.198068] tuner 2-0061: chip found @ 0xc2 (em28xx #0)
[   19.259307] xc2028 2-0061: creating new instance
[   19.259312] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   19.259323] usb 2-4: firmware: requesting xc3028-v27.fw
[   19.275762] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04713/0x204000
[   19.333444] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   19.338959] xc2028 2-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   19.400758] xc2028 2-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   19.570468]   alloc irq_desc for 29 on node -1
[   19.570472]   alloc kstat_irqs on node -1
[   19.570493] tg3 0000:02:00.0: irq 29 for MSI/MSI-X
[   19.796670] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.856063] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.887175] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   19.913807] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   19.938158] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.099918] type=1505 audit(1264925446.144:5):  operation="profile_load" pid=1237 name="/usr/share/gdm/guest-session/Xsession"
[   20.111055] type=1505 audit(1264925446.156:6):  operation="profile_replace" pid=1238 name="/sbin/dhclient3"
[   20.117262] type=1505 audit(1264925446.164:7):  operation="profile_replace" pid=1238 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.117766] type=1505 audit(1264925446.164:8):  operation="profile_replace" pid=1238 name="/usr/lib/connman/scripts/dhclient-script"
[   20.140072] type=1505 audit(1264925446.188:9):  operation="profile_load" pid=1239 name="/usr/bin/evince"
[   20.196817] type=1505 audit(1264925446.244:10):  operation="profile_load" pid=1239 name="/usr/bin/evince-previewer"
[   20.229428] type=1505 audit(1264925446.276:11):  operation="profile_load" pid=1239 name="/usr/bin/evince-thumbnailer"
[   20.237245] Skipping EDID probe due to cached edid
[   20.299888] [drm] TV-14: set mode NTSC 480i 0
[   20.335484] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.576360] [drm] TV-14: set mode NTSC 480i 0
[   20.700752] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.777309] Skipping EDID probe due to cached edid
[   20.839483] [drm] TV-14: set mode NTSC 480i 0
[   20.866268] xc2028 2-0061: Loading firmware for type=(0), id 000000000000b700.
[   20.880143] SCODE (20000000), id 000000000000b700:
[   20.880151] xc2028 2-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   21.136155] [drm] TV-14: set mode NTSC 480i 0
[   21.164142] em28xx #0: Config register raw data: 0x58
[   21.164891] em28xx #0: AC97 vendor ID = 0xffffffff
[   21.165265] em28xx #0: AC97 features = 0x6a90
[   21.165269] em28xx #0: Empia 202 AC97 audio processor detected
[   21.189689] ppdev: user-space parallel port driver
[   21.392513] tvp5150 2-005c: tvp5150am1 detected.
[   21.488895] em28xx #0: v4l2 driver version 0.1.2
[   21.575510] em28xx #0: V4L2 video device registered as /dev/video0
[   21.575514] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   21.599390] usbcore: registered new interface driver snd-usb-audio
[   21.601395] usbcore: registered new interface driver em28xx
[   21.601400] em28xx driver loaded
[   21.671012] tvp5150 2-005c: tvp5150am1 detected.
[   22.010910] xc2028 2-0061: attaching existing instance
[   22.010914] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   22.010916] em28xx #0/2: xc3028 attached
[   22.010919] DVB: registering new adapter (em28xx #0)
[   22.010924] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   22.011257] Successfully loaded em28xx-dvb
[   22.011260] Em28xx: Initialized (Em28xx dvb Extension) extension
[   22.169109] Skipping EDID probe due to cached edid
[   22.229839] [drm] TV-14: set mode NTSC 480i 0
[   22.423530] [drm] TV-14: set mode NTSC 480i 0
[   22.572809] Skipping EDID probe due to cached edid
[   22.633517] [drm] TV-14: set mode NTSC 480i 0
[   22.816013] [drm] TV-14: set mode NTSC 480i 0
[   22.976856] Skipping EDID probe due to cached edid
[   23.037566] [drm] TV-14: set mode NTSC 480i 0
[   23.220082] [drm] TV-14: set mode NTSC 480i 0
[   82.465222] Skipping EDID probe due to cached edid
[   82.525974] [drm] TV-14: set mode NTSC 480i 0
[   82.708632] [drm] TV-14: set mode NTSC 480i 0
[   82.849004] Skipping EDID probe due to cached edid
[   82.909723] [drm] TV-14: set mode NTSC 480i 0
[   83.092434] [drm] TV-14: set mode NTSC 480i 0
[   83.236852] Skipping EDID probe due to cached edid
[   83.297573] [drm] TV-14: set mode NTSC 480i 0
[   83.480167] [drm] TV-14: set mode NTSC 480i 0
[   85.617651] Skipping EDID probe due to cached edid
[   85.678734] [drm] TV-14: set mode NTSC 480i 0
[   86.115735] [drm] TV-14: set mode NTSC 480i 0
[   86.924234] 
-----------------------------
scan only finds 4 channels from >12 possible. With an Ubuntu 9.04 on the same machine I can find and watch all channels. Me-TV finds no channel at all and kaffeine finds 4 but can only display one channel correctly.

Possibly there is a Problem with switching to another transponder because scan complains about:

WARNING: >>> tuning failed!!!
>>> tune to: 618000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!

I know, the stick is detected as a Zarlink, but this never was a Problem in Ubuntu 9.04

I'm now using Kernel 2.6.32-12-generic

If anyone has this hardware up and running, please give me hint. 

Thanks.

---

