---
title: "hp Pavilion 15-cs0700ng"
date: 2019-03-08
forum: Hardware
---

### Post by eriolbrumel on 2019-03-08
Dear Experts,

I have a Notebook hp Pavilion 15-cs0700ng running Kubuntu 18.10 (and Win10 in dualboot, but Windows is not used).

Installation worked very well. Battery time is not perfect (maybe someone has ideas to improve?), but ok.

Only issue was that Wifi was not detected out of the box ([SIZE=1][FONT=arial narrow][COLOR=#111111]Realtek RTL8821CE[/COLOR][/FONT][/SIZE]) but there are solutions on github that make this chip work with Linux (kernel module).

However, during startup I receive an error message on screen:

```
PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
```

I also attach a dmesg snip below where you can see that this error appears several times in a row during startup. I would like to understand what is wrong, and how I could solve this?

Thanks for your time and help!

Eriol

Here is the dmesg snip:


```
[    3.769496] RTW: rtw_read_efuse_from_file /system/etc/wifi/wifi_efuse_8821ce.map is not readable[    3.769504] RTW: hal_com_config_channel_plan chplan:0x7F
[    3.776643] RTW: rtw_regsty_chk_target_tx_power_valid return _FALSE for band:0, path:0, rs:0, t:-1
[    3.776927] RTW: rtw_ndev_init(wlan0) if1 mac_addr=80:2b:f9:73:c2:13
[    3.777212] RTW: module init ret=0
[    3.804187] kvm: disabled by bios
[    3.817935] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.823294] intel_rapl: Found RAPL domain package
[    3.823296] intel_rapl: Found RAPL domain core
[    3.823297] intel_rapl: Found RAPL domain uncore
[    3.823298] intel_rapl: Found RAPL domain dram
[    3.827881] hp_wmi: query 0xd returned error 0x5
[    3.827924] input: HP WMI hotkeys as /devices/virtual/input/input11
[    3.851885] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC295: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.851887] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.851888] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.851889] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.851890] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.851891] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[    3.851892] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    3.862111] rtl8821ce 0000:02:00.0 wlo1: renamed from wlan0
[    3.902532] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    3.902588] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    3.902640] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    3.902685] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    3.902732] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    3.902774] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
[    3.902822] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[    4.338548] Adding 10238972k swap on /dev/sdb5.  Priority:-2 extents:1 across:10238972k SSFS
[    4.713284] media: Linux media interface: v0.10
[    4.715422] Bluetooth: Core ver 2.22
[    4.715437] NET: Registered protocol family 31
[    4.715438] Bluetooth: HCI device and connection manager initialized
[    4.715441] Bluetooth: HCI socket layer initialized
[    4.715443] Bluetooth: L2CAP socket layer initialized
[    4.715448] Bluetooth: SCO socket layer initialized
[    4.718262] videodev: Linux video capture interface: v2.00
[    4.721683] usbcore: registered new interface driver btusb
[    4.722737] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000c lmp_ver=08 lmp_subver=8821
[    4.722739] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821c_config.bin
[    4.724645] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821c_fw.bin
[    4.725727] Bluetooth: hci0: rom_version status=0 version=1
[    4.725734] Bluetooth: hci0: cfg_sz 10, total size 21678
[    4.860952] uvcvideo: Found UVC 1.00 device HP Wide Vision HD Camera (0408:5300)
[    4.864361] uvcvideo 1-3:1.0: Entity type for entity Extension 4 was not initialized!
[    4.864362] uvcvideo 1-3:1.0: Entity type for entity Processing 2 was not initialized!
[    4.864363] uvcvideo 1-3:1.0: Entity type for entity Camera 1 was not initialized!
[    4.864460] input: HP Wide Vision HD Camera: HP Wi as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input19
[    4.864543] usbcore: registered new interface driver uvcvideo
[    4.864544] USB Video Class driver (1.1.1)
[    5.412854] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    5.478635] audit: type=1400 audit(1552024906.824:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=979 comm="apparmor_parser"
[    5.478661] audit: type=1400 audit(1552024906.824:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=980 comm="apparmor_parser"
[    5.479143] audit: type=1400 audit(1552024906.824:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=982 comm="apparmor_parser"
[    5.480742] audit: type=1400 audit(1552024906.828:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=983 comm="apparmor_parser"
[    5.480745] audit: type=1400 audit(1552024906.828:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=983 comm="apparmor_parser"
[    5.480779] audit: type=1400 audit(1552024906.828:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=978 comm="apparmor_parser"
[    5.480781] audit: type=1400 audit(1552024906.828:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=978 comm="apparmor_parser"
[    5.480782] audit: type=1400 audit(1552024906.828:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=978 comm="apparmor_parser"
[    5.481561] audit: type=1400 audit(1552024906.828:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=997 comm="apparmor_parser"
[    5.482614] audit: type=1400 audit(1552024906.828:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=984 comm="apparmor_parser"
[    5.865460] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.865461] Bluetooth: BNEP filters: protocol multicast
[    5.865464] Bluetooth: BNEP socket layer initialized
[    6.162929] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    6.226543] r8169 0000:03:00.0 eno1: link down
[    6.226648] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    6.229536] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    6.245738] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[    6.245750] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[    6.245781] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[    6.245800] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[    6.245818] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[    6.245843] pcieport 0000:00:1c.4: broadcast error_detected message
[    6.245863] pcieport 0000:00:1c.4: AER: Device recovery failed
[    6.733526] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[    6.733884] RTW: WARN Unhandled ISR = 20000000, 0, 0
[    6.733945] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    6.830943] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    9.124081] RTW: nolinked power save enter
[   10.018479] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   10.018494] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   10.018497] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   10.018498] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   10.018500] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   10.018508] pcieport 0000:00:1c.4: broadcast error_detected message
[   10.018529] pcieport 0000:00:1c.4: AER: Device recovery failed
[   10.497546] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   10.497667] RTW: nolinked power save leave
[   10.497687] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   12.788165] RTW: nolinked power save enter
[   13.711032] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   13.711039] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   13.711043] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   13.711045] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   13.711046] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   13.711053] pcieport 0000:00:1c.4: broadcast error_detected message
[   13.711066] pcieport 0000:00:1c.4: AER: Device recovery failed
[   14.197598] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   14.197772] RTW: nolinked power save leave
[   14.197808] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   14.828045] RTW: nolinked power save enter
[   15.339064] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   15.339080] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   15.339091] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   15.339098] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   15.339105] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   15.339116] pcieport 0000:00:1c.4: broadcast error_detected message
[   15.339178] pcieport 0000:00:1c.4: AER: Device recovery failed
[   15.817408] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   15.817533] RTW: nolinked power save leave
[   15.817554] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   17.050680] Bluetooth: RFCOMM TTY layer initialized
[   17.050686] Bluetooth: RFCOMM socket layer initialized
[   17.050689] Bluetooth: RFCOMM ver 1.11
[   18.112074] RTW: nolinked power save enter
[   18.117255] kauditd_printk_skb: 19 callbacks suppressed
[   18.117257] audit: type=1400 audit(1552024919.464:31): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" name="/sys/devices/system/node/" pid=2374 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   18.146440] audit: type=1400 audit(1552024919.492:32): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" name="/etc/mysql/my.cnf.fallback" pid=2374 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   18.315601] audit: type=1400 audit(1552024919.660:33): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" name="/sys/devices/system/node/" pid=2377 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   18.627119] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   18.627139] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   18.627150] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   18.627157] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   18.627165] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   18.627178] pcieport 0000:00:1c.4: broadcast error_detected message
[   18.627245] pcieport 0000:00:1c.4: AER: Device recovery failed
[   19.113565] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   19.113737] RTW: nolinked power save leave
[   19.113810] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   21.416047] RTW: nolinked power save enter
[   21.926523] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   21.926542] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   21.926552] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   21.926559] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   21.926567] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   21.926578] pcieport 0000:00:1c.4: broadcast error_detected message
[   21.926633] pcieport 0000:00:1c.4: AER: Device recovery failed
[   22.413716] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   22.413892] RTW: nolinked power save leave
[   22.413952] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   24.716050] RTW: nolinked power save enter
[   25.229708] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   25.229722] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   25.229726] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   25.229729] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   25.229733] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   25.229743] pcieport 0000:00:1c.4: broadcast error_detected message
[   25.229774] pcieport 0000:00:1c.4: AER: Device recovery failed
[   25.713467] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   25.713600] RTW: nolinked power save leave
[   25.713620] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   28.012099] RTW: nolinked power save enter
[   28.527278] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   28.527294] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   28.527302] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   28.527306] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   28.527308] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   28.527318] pcieport 0000:00:1c.4: broadcast error_detected message
[   28.527375] pcieport 0000:00:1c.4: AER: Device recovery failed
[   29.013407] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   29.013527] RTW: nolinked power save leave
[   29.013541] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   31.304105] RTW: nolinked power save enter
[   31.818938] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   31.818950] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   31.818954] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   31.818956] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   31.818958] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   31.818966] pcieport 0000:00:1c.4: broadcast error_detected message
[   31.818989] pcieport 0000:00:1c.4: AER: Device recovery failed
[   32.297436] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   32.297579] RTW: nolinked power save leave
[   32.297634] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   34.600068] RTW: nolinked power save enter
[   35.113698] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   35.113710] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   35.113713] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   35.113715] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   35.113716] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   35.113722] pcieport 0000:00:1c.4: broadcast error_detected message
[   35.113743] pcieport 0000:00:1c.4: AER: Device recovery failed
[   35.593381] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   35.593502] RTW: nolinked power save leave
[   35.593516] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   37.888101] RTW: nolinked power save enter
[   38.404218] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   38.404233] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   38.404243] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   38.404249] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   38.404256] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   38.404265] pcieport 0000:00:1c.4: broadcast error_detected message
[   38.404324] pcieport 0000:00:1c.4: AER: Device recovery failed
[   38.885554] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   38.885722] RTW: nolinked power save leave
[   38.885784] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   41.176084] RTW: nolinked power save enter
[   41.692679] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   41.692695] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   41.692706] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   41.692713] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   41.692720] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   41.692730] pcieport 0000:00:1c.4: broadcast error_detected message
[   41.692788] pcieport 0000:00:1c.4: AER: Device recovery failed
[   42.173662] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   42.173833] RTW: nolinked power save leave
[   42.173903] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   44.004392] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   44.464048] RTW: nolinked power save enter
[   44.490726] pcieport 0000:00:1c.4: AER: Uncorrected (Non-Fatal) error received: 0000:00:1c.4
[   44.490738] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
[   44.490741] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00008000/00010000
[   44.490743] pcieport 0000:00:1c.4:    [15] Completer Abort        (First)
[   44.490745] pcieport 0000:00:1c.4:   TLP Header: 00000000 00000000 00000000 00000000
[   44.490753] pcieport 0000:00:1c.4: broadcast error_detected message
[   44.490773] pcieport 0000:00:1c.4: AER: Device recovery failed
[   44.973349] RTW: wlo1- hw port(0) mac_addr =80:2b:f9:73:c2:13
[   44.973474] RTW: nolinked power save leave
[   44.973492] RTW: WARN Unhandled ISR = 20000000, 0, 0
[   45.601032] RTW: rtw_set_802_11_connect(wlo1)  fw_state=0x00000000
[   45.655168] RTW: start auth
[   45.657863] RTW: auth success, start assoc
[   45.662310] RTW: assoc success
[   45.665192] RTW: recv eapol packet
[   45.665453] RTW: send eapol packet
[   45.670948] RTW: recv eapol packet
[   45.671065] RTW: send eapol packet
[   45.671132] RTW: set pairwise key camid:4, addr:7c:ff:4d:84:d2:e1, kid:0, type:AES
[   45.671290] RTW: set group key camid:5, addr:7c:ff:4d:84:d2:e1, kid:1, type:AES
[   45.671320] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   53.647051] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[   53.655915] JFS: nTxBlock = 8192, nTxLock = 65536
[   53.666222] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[   53.681682] QNX4 filesystem 0.2.3 registered.
[   53.736043] raid6: sse2x1   gen() 10331 MB/s
[   53.784044] raid6: sse2x1   xor()  8801 MB/s
[   53.832042] raid6: sse2x2   gen() 14967 MB/s
[   53.880043] raid6: sse2x2   xor() 10005 MB/s
[   53.928043] raid6: sse2x4   gen() 17323 MB/s
[   53.976037] raid6: sse2x4   xor() 10568 MB/s
[   54.024041] raid6: avx2x1   gen() 24095 MB/s
[   54.072045] raid6: avx2x1   xor() 16714 MB/s
[   54.120044] raid6: avx2x2   gen() 29025 MB/s
[   54.168042] raid6: avx2x2   xor() 18377 MB/s
[   54.216041] raid6: avx2x4   gen() 33285 MB/s
[   54.264036] raid6: avx2x4   xor() 20243 MB/s
[   54.264037] raid6: using algorithm avx2x4 gen() 33285 MB/s
[   54.264037] raid6: .... xor() 20243 MB/s, rmw enabled
[   54.264038] raid6: using avx2x2 recovery algorithm
[   54.266501] xor: automatically using best checksumming function   avx       
[   54.285413] Btrfs loaded, crc32c=crc32c-intel
```

---

