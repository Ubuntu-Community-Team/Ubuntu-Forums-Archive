---
title: "MSI TV @nywhere"
date: 2011-12-19
forum: Hardware
---

### Post by mnorgate on 2011-12-19
Hi,

I have been trying to get my TV card working with little success, it is an MSI TV @nywhere. Any advice on steps to take.

dmesg output

```

[    5.280293] Linux video capture interface: v2.00
[    5.286103] cfg80211: Calling CRDA to update world regulatory domain
[    5.286455] IR NEC protocol handler initialized
[    5.288687] IR RC5(x) protocol handler initialized
[    5.291423] saa7130/34: v4l2 driver version 0.2.16 loaded
[    5.292523] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 16
[    5.292539] saa7134 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 16 (level, low) -> IRQ 16
[    5.292542] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 16, latency: 64, mmio: 0xf7ff7800
[    5.292547] saa7133[0]: subsystem: 4e42:3306, board: Philips Tiger - S Reference design [card=109,insmod option]
[    5.292566] saa7133[0]: board init: gpio is 210000
[    5.292872] IR RC6 protocol handler initialized
[    5.294436] IR JVC protocol handler initialized
[    5.296488] IR Sony protocol handler initialized
[    5.300353] lirc_dev: IR Remote Control driver registered, major 250 
[    5.300471] IR LIRC bridge handler initialized
[    5.314327] MCE: In-kernel MCE decoding enabled.
[    5.319405] EDAC MC: Ver: 2.1.0
[    5.323728] AMD64 EDAC driver v3.4.0
[    5.324634] type=1400 audit(1324296444.806:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=840 comm="apparmor_parser"
[    5.324931] type=1400 audit(1324296444.806:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=840 comm="apparmor_parser"
[    5.325102] type=1400 audit(1324296444.806:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=840 comm="apparmor_parser"
[    5.327162] EDAC amd64: DRAM ECC disabled.
[    5.327169] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    5.327170]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    5.327171]  (Note that use of the override may cause unknown side effects.)
[    5.338282] Bluetooth: Core ver 2.16
[    5.338303] NET: Registered protocol family 31
[    5.338304] Bluetooth: HCI device and connection manager initialized
[    5.338306] Bluetooth: HCI socket layer initialized
[    5.338307] Bluetooth: L2CAP socket layer initialized
[    5.339223] Bluetooth: SCO socket layer initialized
[    5.340830] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    5.341065] usbcore: registered new interface driver btusb
[    5.354146] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[    5.354151] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[    5.354279] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    5.354283] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[    5.354286] hda_intel: Disabling MSI
[    5.354315] HDA Intel 0000:00:07.0: setting latency timer to 64
[    5.416469] cfg80211: World regulatory domain updated:
[    5.416480] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.416482] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.416484] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.416485] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.416487] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.416488] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.443336] usbcore: registered new interface driver usbhid
[    5.443338] usbhid: USB HID core driver
[    5.444013] saa7133[0]: i2c eeprom 00: 42 4e 06 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    5.444018] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[    5.444023] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 ed ff ff ff ff
[    5.444027] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444031] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 32 15 ff ff ff ff
[    5.444035] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444039] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444042] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444046] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444050] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444054] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444058] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444062] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444066] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444070] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.444074] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.451211] input: Microsoft Microsoft Wireless Optical DesktopÂ® 2.10 as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input2
[    5.451286] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical DesktopÂ® 2.10] on usb-0000:00:02.0-1/input0
[    5.452678] EXT4-fs (sdd5): re-mounted. Opts: errors=remount-ro
[    5.454892] i2c-core: driver [tuner] using legacy suspend method
[    5.454894] i2c-core: driver [tuner] using legacy resume method
[    5.470612] input: Microsoft Microsoft Wireless Optical DesktopÂ® 2.10 as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.1/input/input3
[    5.470700] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical DesktopÂ® 2.10] on usb-0000:00:02.0-1/input1
[    5.484040] tuner 2-004b: Tuner -1 found with type(s) Radio TV.
[    5.500622] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[    5.501154] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.531769] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[    5.535669] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    5.564032] tda829x 2-004b: setting tuner address to 61
[    5.608552] EXT4-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
[    5.632022] tda829x 2-004b: type set to tda8290+75a
[    5.632856] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[    5.667141] EXT4-fs (sdc1): warning: maximal mount count reached, running e2fsck is recommended
[    5.692117] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    5.731432] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[    6.044029] hda_codec: ALC1200: BIOS auto-probing.
[    6.416213] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input4
[    6.738788] type=1400 audit(1324296446.218:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1214 comm="apparmor_parser"
[    6.739087] type=1400 audit(1324296446.218:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1214 comm="apparmor_parser"
[    6.739257] type=1400 audit(1324296446.218:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1214 comm="apparmor_parser"
[    6.741740] type=1400 audit(1324296446.222:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1212 comm="apparmor_parser"
[    6.741931] type=1400 audit(1324296446.222:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1211 comm="apparmor_parser"
[    6.744754] type=1400 audit(1324296446.226:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1220 comm="apparmor_parser"
[    6.745104] type=1400 audit(1324296446.226:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1220 comm="apparmor_parser"
[    6.752748] type=1400 audit(1324296446.234:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1219 comm="apparmor_parser"
[    6.752864] type=1400 audit(1324296446.234:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1221 comm="apparmor_parser"
[    6.753047] type=1400 audit(1324296446.234:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1219 comm="apparmor_parser"
[    6.812787] init: failsafe main process (1166) killed by TERM signal
[    6.813316] init: apport pre-start process (1265) terminated with status 1
[    6.813549] init: freenx-server pre-start process (1271) terminated with status 127
[    6.825234] init: apport post-stop process (1306) terminated with status 1
[    6.825545] init: freenx-server post-stop process (1311) terminated with status 127
[    6.886800] forcedeth 0000:00:0a.0: irq 41 for MSI/MSI-X
[    9.380277] saa7133[0]: dsp access error
[    9.444096] saa7133[0]: registered device video0 [v4l2]
[    9.444115] saa7133[0]: registered device vbi0
[    9.444135] saa7133[0]: registered device radio0
[    9.444432] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[    9.444437] rt61pci 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    9.446234] saa7134 ALSA driver for DMA sound loaded
[    9.446257] saa7133[0]/alsa: saa7133[0] at 0xf7ff7800 irq 16 registered as card -2
[    9.448462] dvb_init() allocating 1 frontend
[    9.451057] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    9.451059] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451060] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    9.451062] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451063] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    9.451065] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451066] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    9.451067] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451069] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    9.451070] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451071] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    9.451073] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451074] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    9.451076] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451077] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    9.451078] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451080] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    9.451081] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451082] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    9.451084] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451085] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    9.451087] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451088] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    9.451090] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451091] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    9.451092] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.451094] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    9.451095] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    9.453344] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    9.453683] Registered led device: rt61pci-phy0::radio
[    9.453696] Registered led device: rt61pci-phy0::assoc
[    9.456041] DVB: registering new adapter (saa7133[0])
[    9.456045] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[    9.472274] udevd[622]: renamed network interface wlan0 to wlan1
[    9.528030] tda1004x: setting up plls for 48MHz sampling clock
[    9.528733] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    9.932855] tda1004x: found firmware revision ea -- invalid
[    9.932858] tda1004x: trying to boot from eeprom
[   10.236850] tda1004x: found firmware revision ea -- invalid
[   10.236853] tda1004x: waiting for firmware upload...
[   10.239136] tda1004x: no firmware upload (timeout or file not found?)
[   10.239139] tda1004x: firmware upload failed
[   10.239833] saa7133[0]/dvb: could not access tda8290 I2C gate
[   10.240118] saa7133[0]/dvb: could not access tda8290 I2C gate
[   10.240120] tda827x_probe_version: could not read from tuner at addr: 0xc2

```

scan /usr/share/dvb/dvb-t/uk-Rowridge output

```

scanning /usr/share/dvb/dvb-t/uk-Rowridge
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 489833000 0 3 9 1 0 0 0
initial transponder 530000000 0 2 9 3 0 0 0
initial transponder 545833000 0 2 9 3 0 0 0
initial transponder 562167000 0 3 9 1 0 0 0
initial transponder 513833000 0 3 9 1 0 0 0
initial transponder 570167000 0 3 9 1 0 0 0
>>> tune to: 489833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 530000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 545833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 562167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 513833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 570167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.


``` name=

---

