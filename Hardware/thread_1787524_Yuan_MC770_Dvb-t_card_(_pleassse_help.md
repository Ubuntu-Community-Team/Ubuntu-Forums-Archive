---
title: "Yuan MC770 Dvb-t card :( pleassse help"
date: 2011-06-21
forum: Hardware
---

### Post by clgamer on 2011-06-21
Hi All,
I have recently migrated to ubuntu and my Dvb-t card has stopped working. it detected the device and let me download the driver for it but whenever I use any application to scan for channels it never gets a signal. So far I have tried Me Tv, VLC and mythtv (which i didn't like). 

When I type dmesg it shows the card present "initialized and connected"

Is there anything I am missing? I have spent around 18 hours trying to work this out any help would be reaaaaaaly appreciated.

its a Yuan MC770

Thanks in advance

---

### Post by clgamer on 2011-06-21
K so I just tried Kaffeine and it shows 70%+ signal strength and SNR 1%
But still finds no channels, I set the DVB settings to UK, crystal palace but nothing... 

Anybody 

](*,)  no matter how much I try it just doesn't seem to work, I have the latest version of kernel installed as well.... was almost 100% happy with ubuntu until this

dmesg reads:


00 mBm)
[   12.205073] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.205080] i915 0000:00:02.0: setting latency timer to 64
[   12.212281] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   12.212533] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.219010] dib0700: loaded with support for 15 different device-types
[   12.234033] dvb-usb: found a 'YUAN High-Tech STK7700PH' in warm state.
[   12.234200] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.239317] DVB: registering new adapter (YUAN High-Tech STK7700PH)
[   12.243984] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   12.243992] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.244079] [drm] Driver supports precise vblank timestamp query.
[   12.278815] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.278830] ath5k 0000:02:00.0: setting latency timer to 64
[   12.278884] ath5k 0000:02:00.0: registered as 'phy0'
[   12.399490] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.487153] composite sync not supported
[   12.566143] Console: switching to colour frame buffer device 128x48
[   12.566171] fb0: inteldrmfb frame buffer device
[   12.566173] drm: registered panic notifier
[   12.567790] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   12.567990] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[   12.569199] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.569265] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.569337] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.569366] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.764048] fixme: max PWM is zero.
[   12.779535] ath: EEPROM regdomain: 0x60
[   12.779539] ath: EEPROM indicates we should expect a direct regpair map
[   12.779543] ath: Country alpha2 being used: 00
[   12.779545] ath: Regpair used: 0x60
[   12.779576] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.779580] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779582] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.779585] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779587] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.779590] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779592] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.779594] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779597] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.779599] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779601] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.779604] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779606] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.779609] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779611] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.779614] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779616] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.779618] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779621] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.779623] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779626] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.779628] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779631] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.779633] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779636] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.779638] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779641] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.779643] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.779850] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   12.828830] hda_codec: ALC888: BIOS auto-probing.
[   12.839405] composite sync not supported
[   12.907568] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   12.912875] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   12.925091] EXT4-fs warning (device sda1): release_blocks_on_commit:2672: discard not supported, disabling
[   12.950361] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.984163] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   13.008302] xc2028 17-0061: creating new instance
[   13.008306] xc2028 17-0061: type set to XCeive xc2028/xc3028 tuner
[   13.044023] Registered IR keymap rc-dib0700-rc5
[   13.044260] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/rc/rc0/input6
[   13.044398] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/rc/rc0
[   13.044525] dvb-usb: schedule remote query interval to 50 msecs.
[   13.044532] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.
[   13.044641] dib0700: rc submit urb failed
[   13.044642] 
[   13.044684] usbcore: registered new interface driver dvb_usb_dib0700
[   13.186860] ppdev: user-space parallel port driver
[   13.497864] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[   13.521256] composite sync not supported
[   13.704442] composite sync not supported
[   13.715144] EXT4-fs warning (device sda1): release_blocks_on_commit:2672: discard not supported, disabling
[   14.832010] composite sync not supported
[   15.015874] composite sync not supported
[   15.199873] composite sync not supported
[   15.387870] composite sync not supported
[   15.752126] composite sync not supported
[   18.343317] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[   21.142993] EXT4-fs warning (device sda1): release_blocks_on_commit:2672: discard not supported, disabling
[   21.473210] composite sync not supported
[   31.491943] wlan0: authenticate with 00:0e:9b:a2:1a:ea (try 1)
[   31.493865] wlan0: authenticated
[   31.493903] wlan0: associate with 00:0e:9b:a2:1a:ea (try 1)
[   31.496485] wlan0: RX AssocResp from 00:0e:9b:a2:1a:ea (capab=0x411 status=0 aid=2)
[   31.496490] wlan0: associated
[   31.497166] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.464017] wlan0: no IPv6 routers present
[   80.006670] xc2028 17-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   80.033195] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[   85.917754] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (208), id 0000000000000000.
[   86.021928] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.
[  124.545079] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  130.430150] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (208), id 0000000000000000.
[  130.534700] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.
[  253.481090] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  259.365908] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (208), id 0000000000000000.
[  259.470083] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.
[  636.679829] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  642.565762] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (208), id 0000000000000000.
[  642.669936] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.

---

### Post by clgamer on 2011-06-21
bit puzzled it seems present but does not function:confused:: 

lsmod | grep dvb 
dvb_usb_dib0700        62306  0 
dib7000p               27746  2 dvb_usb_dib0700
dib0090                23186  1 dvb_usb_dib0700
dib7000m               22939  1 dvb_usb_dib0700
dib0070                18078  1 dvb_usb_dib0700
dvb_usb                23658  1 dvb_usb_dib0700
dib8000                37054  1 dvb_usb_dib0700
dvb_core               90587  3 dib7000p,dvb_usb,dib8000
dib3000mc              22898  1 dvb_usb_dib0700
rc_core                25760  10 rc_dib0700_rc5,dvb_usb_dib0700,dvb_usb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder

---

