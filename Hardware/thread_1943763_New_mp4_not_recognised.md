---
title: "New mp4 not recognised?"
date: 2012-03-20
forum: Hardware
---

### Post by jonnyboysmithy on 2012-03-20
I bought a new mp4 player today. Windows 7 says 'usb device not recognised'. On ubuntu nothing happens when I plug it in (when on or off). On windows xp it just recognizes as a memory stick. I have tried using a different cable but no difference. Anything I could do?:confused:

EDIT: Strangely windows7 will recognize it now. Not sure why though.

---

### Post by jonnyboysmithy on 2012-03-20
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 002 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 000: ID 1e74:4641 Coby Electronics Corporation 

```I think the last one on the list is it.

---

### Post by jonnyboysmithy on 2012-03-20
output of dmesg:```
[ 2766.019425] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5adc0
[ 2766.019432] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ae00
[ 2766.019448] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2766.019457] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2766.026818] sd 12:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 2766.027807] sd 12:0:0:0: [sdc] Asking for cache data failed
[ 2766.027818] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 2766.028465] sdc: detected capacity change from 8170504192 to 0
[ 2767.751038] sd 12:0:0:0: [sdc] 15958016 512-byte logical blocks: (8.17 GB/7.60 GiB)
[ 2767.861502] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2767.878374] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ad80
[ 2767.878386] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5adc0
[ 2767.878393] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ae00
[ 2767.878408] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2767.878417] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2767.885801] sd 12:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 2767.886773] sd 12:0:0:0: [sdc] Asking for cache data failed
[ 2767.886783] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 2767.887369] sdc: detected capacity change from 8170504192 to 0
[ 2769.751683] sd 12:0:0:0: [sdc] 15958016 512-byte logical blocks: (8.17 GB/7.60 GiB)
[ 2769.864578] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2769.881311] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ad80
[ 2769.881322] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5adc0
[ 2769.881329] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ae00
[ 2769.881345] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2769.881354] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2770.000422] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2770.017507] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ad80
[ 2770.017518] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5adc0
[ 2770.017525] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ae00
[ 2770.017541] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2770.017550] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2770.136402] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2775.149413] usb 3-1: device descriptor read/8, error -110
[ 2780.266682] usb 3-1: device descriptor read/8, error -110
[ 2780.482695] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2785.496021] usb 3-1: device descriptor read/8, error -110
[ 2790.613440] usb 3-1: device descriptor read/8, error -110
[ 2790.829382] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2795.842743] usb 3-1: device descriptor read/8, error -110
[ 2800.960123] usb 3-1: device descriptor read/8, error -110
[ 2801.175982] usb 3-1: reset high-speed USB device number 23 using xhci_hcd
[ 2806.189378] usb 3-1: device descriptor read/8, error -110
[ 2811.306735] usb 3-1: device descriptor read/8, error -110
[ 2811.410507] usb 3-1: USB disconnect, device number 23
[ 2811.410585] sd 12:0:0:0: Device offlined - not ready after error recovery
[ 2811.410707] sd 12:0:0:0: [sdc] Asking for cache data failed
[ 2811.410715] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 2811.410978] sd 12:0:0:0: [sdc] READ CAPACITY failed
[ 2811.410990] sd 12:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2811.411001] sd 12:0:0:0: [sdc] Sense not available.
[ 2811.411069] sd 12:0:0:0: [sdc] No Caching mode page present
[ 2811.411077] sd 12:0:0:0: [sdc] Assuming drive cache: write through
[ 2811.411087] sdc: detected capacity change from 8170504192 to 0
[ 2811.427338] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ad80
[ 2811.427352] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5adc0
[ 2811.427363] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880213e5ae00
[ 2811.542390] usb 3-1: new high-speed USB device number 24 using xhci_hcd
[ 2816.556065] usb 3-1: device descriptor read/8, error -110
[ 2821.673445] usb 3-1: device descriptor read/8, error -110
[ 2821.889119] usb 3-1: new high-speed USB device number 25 using xhci_hcd
[ 2826.902783] usb 3-1: device descriptor read/8, error -110
[ 2832.020181] usb 3-1: device descriptor read/8, error -110
[ 2832.235766] usb 3-1: new high-speed USB device number 26 using xhci_hcd
[ 2837.249356] usb 3-1: device descriptor read/8, error -110
[ 2842.366800] usb 3-1: device descriptor read/8, error -110
[ 2842.582482] usb 3-1: new high-speed USB device number 27 using xhci_hcd
[ 2847.595950] usb 3-1: device descriptor read/8, error -110
[ 2852.713605] usb 3-1: device descriptor read/8, error -110
[ 2852.817233] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 2949.675404] usb 3-1: new high-speed USB device number 28 using xhci_hcd
[ 2949.694658] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2949.694670] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2949.695645] scsi13 : usb-storage 3-1:1.0
[ 2950.696026] scsi 13:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[ 2950.697963] sd 13:0:0:0: Attached scsi generic sg3 type 0
[ 2950.698732] sd 13:0:0:0: [sdc] 15958016 512-byte logical blocks: (8.17 GB/7.60 GiB)
[ 2950.811551] usb 3-1: reset high-speed USB device number 28 using xhci_hcd
[ 2950.828630] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b480
[ 2950.828641] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b4c0
[ 2950.828649] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b500
[ 2950.828663] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2950.828672] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2950.835774] sd 13:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 2950.836768] sd 13:0:0:0: [sdc] Asking for cache data failed
[ 2950.836779] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[ 2950.837552] sdc: detected capacity change from 8170504192 to 0
[ 2950.838188] sd 13:0:0:0: [sdc] Attached SCSI removable disk
[ 2953.665301] sd 13:0:0:0: [sdc] 15958016 512-byte logical blocks: (8.17 GB/7.60 GiB)
[ 2953.778042] usb 3-1: reset high-speed USB device number 28 using xhci_hcd
[ 2953.795044] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b480
[ 2953.795055] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b4c0
[ 2953.795062] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b500
[ 2953.795078] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2953.795086] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2953.913950] usb 3-1: reset high-speed USB device number 28 using xhci_hcd
[ 2953.930986] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b480
[ 2953.930998] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b4c0
[ 2953.931005] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b500
[ 2953.931020] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2953.931029] usb 3-1: ep 0x82 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2954.049987] usb 3-1: reset high-speed USB device number 28 using xhci_hcd
[ 2959.062885] usb 3-1: device descriptor read/8, error -110
[ 2964.180153] usb 3-1: device descriptor read/8, error -110
[ 2964.396147] usb 3-1: reset high-speed USB device number 28 using xhci_hcd
[ 2969.409495] usb 3-1: device descriptor read/8, error -110
[ 2969.531163] usb 3-1: device descriptor read/8, error -71
[ 2969.689174] usb 3-1: USB disconnect, device number 28
[ 2969.690543] scsi 13:0:0:0: killing request
[ 2969.690571] scsi 13:0:0:0: [sdc] Asking for cache data failed
[ 2969.690575] scsi 13:0:0:0: [sdc] Assuming drive cache: write through
[ 2969.705187] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b480
[ 2969.705192] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b4c0
[ 2969.705195] xhci_hcd 0000:19:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021882b500
[ 4851.827807] wlan0: deauthenticating from 00:22:75:22:bd:f4 by local choice (reason=3)
[ 4851.922528] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4851.922534] cfg80211: Restoring regulatory settings
[ 4851.922543] cfg80211: Calling CRDA to update world regulatory domain
[ 4851.925873] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 4851.925876] cfg80211: World regulatory domain updated:
[ 4851.925878] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4851.925881] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4851.925884] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4851.925886] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4851.925889] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4851.925891] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4855.170903] wlan0: authenticate with 00:22:75:22:bd:f4 (try 1)
[ 4855.173390] wlan0: authenticated
[ 4855.173955] wlan0: associate with 00:22:75:22:bd:f4 (try 1)
[ 4855.181850] wlan0: RX ReassocResp from 00:22:75:22:bd:f4 (capab=0x411 status=0 aid=1)
[ 4855.181854] wlan0: associated
[ 4863.116739] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 00:22:75:22:bd:f4 tid = 0
[ 6861.051875] wlan0: deauthenticating from 00:22:75:22:bd:f4 by local choice (reason=3)
[ 6861.167285] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 6861.167298] cfg80211: Restoring regulatory settings
[ 6861.167315] cfg80211: Calling CRDA to update world regulatory domain
[ 6861.177557] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 6861.177571] cfg80211: World regulatory domain updated:
[ 6861.177576] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6861.177585] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6861.177594] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6861.177603] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6861.177611] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6861.177620] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6864.390983] wlan0: authenticate with 00:22:75:22:bd:f4 (try 1)
[ 6864.399033] wlan0: authenticated
[ 6864.399699] wlan0: associate with 00:22:75:22:bd:f4 (try 1)
[ 6864.403824] wlan0: RX ReassocResp from 00:22:75:22:bd:f4 (capab=0x411 status=0 aid=1)
[ 6864.403833] wlan0: associated
[ 6867.651526] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 00:22:75:22:bd:f4 tid = 0
[ 9143.517420] usb 2-1.1: new high-speed USB device number 14 using ehci_hcd
[ 9143.611196] scsi14 : usb-storage 2-1.1:1.0
[ 9144.609996] scsi 14:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[ 9144.611448] sd 14:0:0:0: Attached scsi generic sg3 type 0
[ 9144.612844] sd 14:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.16 GB/7.60 GiB)
[ 9144.688744] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9144.864515] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9145.040562] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9145.141372] sd 14:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 9145.142460] sd 14:0:0:0: [sdc] Asking for cache data failed
[ 9145.142471] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 9145.143805] sdc: detected capacity change from 8166309888 to 0
[ 9145.147747] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[ 9146.772402] sd 14:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.16 GB/7.60 GiB)
[ 9146.843614] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9151.933002] usb 2-1.1: device descriptor read/all, error -110
[ 9152.004939] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9167.069291] usb 2-1.1: device descriptor read/64, error -110
[ 9182.237551] usb 2-1.1: device descriptor read/64, error -110
[ 9182.413533] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9187.430816] usb 2-1.1: device descriptor read/8, error -110
[ 9192.548137] usb 2-1.1: device descriptor read/8, error -110
[ 9192.724063] usb 2-1.1: reset high-speed USB device number 14 using ehci_hcd
[ 9197.741436] usb 2-1.1: device descriptor read/8, error -110
[ 9202.858730] usb 2-1.1: device descriptor read/8, error -110
[ 9202.963589] sd 14:0:0:0: Device offlined - not ready after error recovery
[ 9202.963674] usb 2-1.1: USB disconnect, device number 14
[ 9202.963684] sd 14:0:0:0: rejecting I/O to offline device
[ 9202.963704] sd 14:0:0:0: [sdc] Asking for cache data failed
[ 9202.963711] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 9203.034678] usb 2-1.1: new high-speed USB device number 15 using ehci_hcd
[ 9218.098997] usb 2-1.1: device descriptor read/64, error -110
[ 9233.267234] usb 2-1.1: device descriptor read/64, error -110
[ 9233.443147] usb 2-1.1: new high-speed USB device number 16 using ehci_hcd
[ 9248.507238] usb 2-1.1: device descriptor read/64, error -110
[ 9263.675546] usb 2-1.1: device descriptor read/64, error -110
[ 9263.851599] usb 2-1.1: new high-speed USB device number 17 using ehci_hcd
[ 9268.868904] usb 2-1.1: device descriptor read/8, error -110
[ 9273.986117] usb 2-1.1: device descriptor read/8, error -110
[ 9274.162183] usb 2-1.1: new high-speed USB device number 18 using ehci_hcd
[ 9279.179595] usb 2-1.1: device descriptor read/8, error -110
[ 9284.296926] usb 2-1.1: device descriptor read/8, error -110
[ 9284.401401] hub 2-1:1.0: unable to enumerate USB device on port 1
[ 9525.780908] usb 2-1.2: new high-speed USB device number 19 using ehci_hcd
[ 9525.874762] scsi15 : usb-storage 2-1.2:1.0
[ 9526.873210] scsi 15:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[ 9526.874954] sd 15:0:0:0: Attached scsi generic sg3 type 0
[ 9526.878745] sd 15:0:0:0: [sdc] 15958016 512-byte logical blocks: (8.17 GB/7.60 GiB)
[ 9526.956246] usb 2-1.2: reset high-speed USB device number 19 using ehci_hcd
[ 9542.020413] usb 2-1.2: device descriptor read/64, error -110
[ 9557.188601] usb 2-1.2: device descriptor read/64, error -110
[ 9557.364547] usb 2-1.2: reset high-speed USB device number 19 using ehci_hcd
[ 9572.428835] usb 2-1.2: device descriptor read/64, error -110
[ 9587.597257] usb 2-1.2: device descriptor read/64, error -110
[ 9587.773038] usb 2-1.2: reset high-speed USB device number 19 using ehci_hcd
[ 9592.790385] usb 2-1.2: device descriptor read/8, error -110
[ 9597.907886] usb 2-1.2: device descriptor read/8, error -110
[ 9598.083817] usb 2-1.2: reset high-speed USB device number 19 using ehci_hcd
[ 9603.101191] usb 2-1.2: device descriptor read/8, error -110
[ 9608.218523] usb 2-1.2: device descriptor read/8, error -110
[ 9608.322981] sd 15:0:0:0: Device offlined - not ready after error recovery
[ 9608.323030] usb 2-1.2: USB disconnect, device number 19
[ 9608.323056] sd 15:0:0:0: [sdc] Write Protect is off
[ 9608.323067] sd 15:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 9608.323093] sd 15:0:0:0: rejecting I/O to offline device
[ 9608.323110] sd 15:0:0:0: [sdc] Asking for cache data failed
[ 9608.323115] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 9608.323613] sd 15:0:0:0: [sdc] READ CAPACITY failed
[ 9608.323623] sd 15:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 9608.323632] sd 15:0:0:0: [sdc] Sense not available.
[ 9608.323706] sd 15:0:0:0: [sdc] No Caching mode page present
[ 9608.323717] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 9608.323724] sdc: detected capacity change from 8170504192 to 0
[ 9608.324012] sd 15:0:0:0: [sdc] Attached SCSI removable disk
[ 9608.399098] usb 2-1.2: new high-speed USB device number 20 using ehci_hcd
[ 9623.462747] usb 2-1.2: device descriptor read/64, error -110
[ 9638.631009] usb 2-1.2: device descriptor read/64, error -110
[ 9638.806899] usb 2-1.2: new high-speed USB device number 21 using ehci_hcd
[ 9653.871055] usb 2-1.2: device descriptor read/64, error -110
[ 9663.478254] hub 2-1:1.0: unable to enumerate USB device on port 2
[ 9946.684700] usb 2-1.2: new high-speed USB device number 22 using ehci_hcd
[ 9961.748860] usb 2-1.2: device descriptor read/64, error -110
[ 9971.760095] hub 2-1:1.0: unable to enumerate USB device on port 2
[ 9975.837504] usb 3-2: new high-speed USB device number 29 using xhci_hcd
[ 9980.851105] usb 3-2: device descriptor read/8, error -110
[ 9985.968533] usb 3-2: device descriptor read/8, error -110
[ 9986.184185] usb 3-2: new high-speed USB device number 30 using xhci_hcd
[ 9991.197853] usb 3-2: device descriptor read/8, error -110
[ 9996.315114] usb 3-2: device descriptor read/8, error -110
[ 9996.530871] usb 3-2: new high-speed USB device number 31 using xhci_hcd
[10001.544587] usb 3-2: device descriptor read/8, error -110
[10006.661961] usb 3-2: device descriptor read/8, error -110
[10006.877554] usb 3-2: new high-speed USB device number 32 using xhci_hcd
[10011.891292] usb 3-2: device descriptor read/8, error -110
[10017.008567] usb 3-2: device descriptor read/8, error -110
[10017.112311] hub 3-0:1.0: unable to enumerate USB device on port 2
[10038.029703] usb 2-1.1: new high-speed USB device number 23 using ehci_hcd
[10038.126457] scsi16 : usb-storage 2-1.1:1.0
[10039.127560] scsi 16:0:0:0: Direct-Access     DSE      MicroDrive 2GB   1.00 PQ: 0 ANSI: 2
[10039.129136] sd 16:0:0:0: Attached scsi generic sg3 type 0
[10039.129632] sd 16:0:0:0: [sdc] 4034560 512-byte logical blocks: (2.06 GB/1.92 GiB)
[10039.130315] sd 16:0:0:0: [sdc] Write Protect is off
[10039.130323] sd 16:0:0:0: [sdc] Mode Sense: 23 00 00 00
[10039.130944] sd 16:0:0:0: [sdc] No Caching mode page present
[10039.130956] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[10039.137003] sd 16:0:0:0: [sdc] No Caching mode page present
[10039.137014] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[10039.218234]  sdc: sdc1
[10039.220887] sd 16:0:0:0: [sdc] No Caching mode page present
[10039.220907] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[10039.220914] sd 16:0:0:0: [sdc] Attached SCSI removable disk
[10236.835600] usb 2-1.2: new high-speed USB device number 24 using ehci_hcd
[10236.929452] scsi17 : usb-storage 2-1.2:1.0
[10237.927855] scsi 17:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[10237.928682] sd 17:0:0:0: Attached scsi generic sg4 type 0
[10237.929967] sd 17:0:0:0: [sdd] 15958016 512-byte logical blocks: (8.17 GB/7.60 GiB)
[10238.006926] usb 2-1.2: reset high-speed USB device number 24 using ehci_hcd
[10253.071256] usb 2-1.2: device descriptor read/64, error -110
[10268.239362] usb 2-1.2: device descriptor read/64, error -110
[10268.415079] usb 2-1.2: reset high-speed USB device number 24 using ehci_hcd
[10283.479531] usb 2-1.2: device descriptor read/64, error -110
[10298.647634] usb 2-1.2: device descriptor read/64, error -110
[10298.823708] usb 2-1.2: reset high-speed USB device number 24 using ehci_hcd
[10303.840975] usb 2-1.2: device descriptor read/8, error -110
[10308.958452] usb 2-1.2: device descriptor read/8, error -110
[10309.134363] usb 2-1.2: reset high-speed USB device number 24 using ehci_hcd
[10314.151873] usb 2-1.2: device descriptor read/8, error -110
[10319.269088] usb 2-1.2: device descriptor read/8, error -110
[10319.373157] sd 17:0:0:0: Device offlined - not ready after error recovery
[10319.373184] sd 17:0:0:0: [sdd] Write Protect is off
[10319.373190] sd 17:0:0:0: [sdd] Mode Sense: 03 00 00 00
[10319.373209] usb 2-1.2: USB disconnect, device number 24
[10319.373214] sd 17:0:0:0: rejecting I/O to offline device
[10319.373223] sd 17:0:0:0: [sdd] Asking for cache data failed
[10319.373227] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[10319.373640] sd 17:0:0:0: [sdd] READ CAPACITY failed
[10319.373645] sd 17:0:0:0: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[10319.373650] sd 17:0:0:0: [sdd] Sense not available.
[10319.373679] sd 17:0:0:0: [sdd] Asking for cache data failed
[10319.373683] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[10319.373688] sdd: detected capacity change from 8170504192 to 0
[10319.373793] sd 17:0:0:0: [sdd] Attached SCSI removable disk
[10319.444974] usb 2-1.2: new high-speed USB device number 25 using ehci_hcd
[10334.509299] usb 2-1.2: device descriptor read/64, error -110
[10349.677526] usb 2-1.2: device descriptor read/64, error -110
[10349.853451] usb 2-1.2: new high-speed USB device number 26 using ehci_hcd
[10364.917611] usb 2-1.2: device descriptor read/64, error -110
[10380.085838] usb 2-1.2: device descriptor read/64, error -110
[10380.261707] usb 2-1.2: new high-speed USB device number 27 using ehci_hcd
[10385.279272] usb 2-1.2: device descriptor read/8, error -110
[10390.396566] usb 2-1.2: device descriptor read/8, error -110
[10390.572458] usb 2-1.2: new high-speed USB device number 28 using ehci_hcd
[10395.589707] usb 2-1.2: device descriptor read/8, error -110
[10400.707192] usb 2-1.2: device descriptor read/8, error -110
[10400.811192] hub 2-1:1.0: unable to enumerate USB device on port 2
[11139.798736] WARNING! power/level is deprecated; use power/control instead
[11139.931395] usb 2-1.1: reset high-speed USB device number 23 using ehci_hcd
[11140.039549] usb 2-1.1: USB disconnect, device number 23
[12770.429574] usb 2-1.2: new high-speed USB device number 29 using ehci_hcd
[12770.523755] scsi18 : usb-storage 2-1.2:1.0
[12771.522479] scsi 18:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[12771.523861] sd 18:0:0:0: Attached scsi generic sg3 type 0
[12771.524938] sd 18:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.16 GB/7.60 GiB)
[12771.600964] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12771.776866] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12771.952779] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12772.128688] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12787.192987] usb 2-1.2: device descriptor read/64, error -110
[12802.361240] usb 2-1.2: device descriptor read/64, error -110
[12802.537135] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12817.601285] usb 2-1.2: device descriptor read/64, error -110
[12832.769450] usb 2-1.2: device descriptor read/64, error -110
[12832.945388] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12837.962767] usb 2-1.2: device descriptor read/8, error -110
[12843.080284] usb 2-1.2: device descriptor read/8, error -110
[12843.256020] usb 2-1.2: reset high-speed USB device number 29 using ehci_hcd
[12848.273405] usb 2-1.2: device descriptor read/8, error -110
[12853.390846] usb 2-1.2: device descriptor read/8, error -110
[12853.495593] sd 18:0:0:0: Device offlined - not ready after error recovery
[12853.495651] sd 18:0:0:0: [sdc] Write Protect is off
[12853.495662] sd 18:0:0:0: [sdc] Mode Sense: 03 00 00 00
[12853.495688] sd 18:0:0:0: rejecting I/O to offline device
[12853.495696] usb 2-1.2: USB disconnect, device number 29
[12853.495714] sd 18:0:0:0: [sdc] Asking for cache data failed
[12853.495719] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[12853.496251] sd 18:0:0:0: [sdc] READ CAPACITY failed
[12853.496261] sd 18:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[12853.496271] sd 18:0:0:0: [sdc] Sense not available.
[12853.496339] sd 18:0:0:0: [sdc] Asking for cache data failed
[12853.496347] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[12853.496358] sdc: detected capacity change from 8166309888 to 0
[12853.496651] sd 18:0:0:0: [sdc] Attached SCSI removable disk
[12853.570835] usb 2-1.2: new high-speed USB device number 30 using ehci_hcd
[12868.638950] usb 2-1.2: device descriptor read/64, error -110
[12883.807404] usb 2-1.2: device descriptor read/64, error -110
[12883.983106] usb 2-1.2: new high-speed USB device number 31 using ehci_hcd
[12899.047402] usb 2-1.2: device descriptor read/64, error -110
[12914.215694] usb 2-1.2: device descriptor read/64, error -110
[12914.391595] usb 2-1.2: new high-speed USB device number 32 using ehci_hcd
[12919.408919] usb 2-1.2: device descriptor read/8, error -110
[12924.526281] usb 2-1.2: device descriptor read/8, error -110
[12924.702234] usb 2-1.2: new high-speed USB device number 33 using ehci_hcd
[12929.719738] usb 2-1.2: device descriptor read/8, error -110
[12934.837038] usb 2-1.2: device descriptor read/8, error -110
[12934.941450] hub 2-1:1.0: unable to enumerate USB device on port 2
[13718.162579] usb 2-1.2: new high-speed USB device number 34 using ehci_hcd
[13727.921687] hub 2-1:1.0: unable to enumerate USB device on port 2
[13733.770594] usb 2-1.2: new high-speed USB device number 35 using ehci_hcd
[13735.809764] hub 2-1:1.0: unable to enumerate USB device on port 2
[13738.376198] usb 2-1.2: new high-speed USB device number 36 using ehci_hcd
[13738.470374] scsi19 : usb-storage 2-1.2:1.0
[13739.468737] scsi 19:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[13739.470184] sd 19:0:0:0: Attached scsi generic sg3 type 0
[13739.472675] sd 19:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.16 GB/7.60 GiB)
[13739.547593] usb 2-1.2: reset high-speed USB device number 36 using ehci_hcd
[13754.611884] usb 2-1.2: device descriptor read/64, error -110
[13769.780160] usb 2-1.2: device descriptor read/64, error -110
[13769.956025] usb 2-1.2: reset high-speed USB device number 36 using ehci_hcd
[13785.020183] usb 2-1.2: device descriptor read/64, error -110
[13800.188232] usb 2-1.2: device descriptor read/64, error -110
[13800.364328] usb 2-1.2: reset high-speed USB device number 36 using ehci_hcd
[13805.381546] usb 2-1.2: device descriptor read/8, error -110
[13810.503006] usb 2-1.2: device descriptor read/8, error -110
[13810.679076] usb 2-1.2: reset high-speed USB device number 36 using ehci_hcd
[13815.696474] usb 2-1.2: device descriptor read/8, error -110
[13820.813763] usb 2-1.2: device descriptor read/8, error -110
[13820.918310] sd 19:0:0:0: Device offlined - not ready after error recovery
[13820.918323] usb 2-1.2: USB disconnect, device number 36
[13820.918420] sd 19:0:0:0: [sdc] Write Protect is off
[13820.918430] sd 19:0:0:0: [sdc] Mode Sense: 03 00 00 00
[13820.918460] sd 19:0:0:0: rejecting I/O to offline device
[13820.918478] sd 19:0:0:0: [sdc] Asking for cache data failed
[13820.918485] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[13820.919095] sd 19:0:0:0: [sdc] READ CAPACITY failed
[13820.919103] sd 19:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[13820.919114] sd 19:0:0:0: [sdc] Sense not available.
[13820.919182] sd 19:0:0:0: [sdc] No Caching mode page present
[13820.919191] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[13820.919202] sdc: detected capacity change from 8166309888 to 0
[13820.919489] sd 19:0:0:0: [sdc] Attached SCSI removable disk
[13820.993513] usb 2-1.2: new high-speed USB device number 37 using ehci_hcd
[13836.058037] usb 2-1.2: device descriptor read/64, error -110
[13851.226143] usb 2-1.2: device descriptor read/64, error -110
[13851.402069] usb 2-1.2: new high-speed USB device number 38 using ehci_hcd
[13866.466346] usb 2-1.2: device descriptor read/64, error -110
[13881.634588] usb 2-1.2: device descriptor read/64, error -110
[13881.810496] usb 2-1.2: new high-speed USB device number 39 using ehci_hcd
[13886.827866] usb 2-1.2: device descriptor read/8, error -110
[13891.945164] usb 2-1.2: device descriptor read/8, error -110
[13892.121123] usb 2-1.2: new high-speed USB device number 40 using ehci_hcd
[13897.138454] usb 2-1.2: device descriptor read/8, error -110
[13902.255991] usb 2-1.2: device descriptor read/8, error -110
[13902.360185] hub 2-1:1.0: unable to enumerate USB device on port 2
[14794.593424] usb 2-1.2: new high-speed USB device number 41 using ehci_hcd
[14794.687221] scsi20 : usb-storage 2-1.2:1.0
[14795.685551] scsi 20:0:0:0: Direct-Access              USB DISK         1.00 PQ: 0 ANSI: 0
[14795.686971] sd 20:0:0:0: Attached scsi generic sg3 type 0
[14795.688159] sd 20:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.16 GB/7.60 GiB)
[14795.764794] usb 2-1.2: reset high-speed USB device number 41 using ehci_hcd
[14795.940543] usb 2-1.2: reset high-speed USB device number 41 using ehci_hcd
[14796.041377] sd 20:0:0:0: [sdc] Test WP failed, assume Write Enabled
[14796.042381] sd 20:0:0:0: [sdc] Asking for cache data failed
[14796.042389] sd 20:0:0:0: [sdc] Assuming drive cache: write through
[14796.043611] sdc: detected capacity change from 8166309888 to 0
[14796.044596] sd 20:0:0:0: [sdc] Attached SCSI removable disk
[14797.867528] sd 20:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.16 GB/7.60 GiB)
[14797.939667] usb 2-1.2: reset high-speed USB device number 41 using ehci_hcd
[14813.003812] usb 2-1.2: device descriptor read/64, error -110
[14828.172221] usb 2-1.2: device descriptor read/64, error -110
[14828.348127] usb 2-1.2: reset high-speed USB device number 41 using ehci_hcd
[14843.412431] usb 2-1.2: device descriptor read/64, error -110

```

---

### Post by jonnyboysmithy on 2012-03-22
Bump

---

### Post by SeijiSensei on 2012-03-22
Not all USB mass storage devices work correctly with Linux. It's a common problem with cell phones connected over USB, for instance.  The log shows the device is recognized, but then it immediately disconnects.  My cell phone displayed similar symptoms.

---

### Post by jonnyboysmithy on 2012-03-27
Is there a known workaround?

---

### Post by SemiExpert on 2012-03-27
Brand?  Model?  Details?

---

### Post by jonnyboysmithy on 2012-04-28
On the back it has  N19 A8705 8gb. Dicksmith brand.

---

### Post by jonnyboysmithy on 2012-04-29
bump

---

### Post by SeijiSensei on 2012-04-29
If the device isn't recognized by Windows there's an even slimmer chance it will be recognized by Linux.  

Have you tried connecting the device to all the USB ports on your computer?  My daughter's HP had one USB 3.0 port that would not connect to older devices. 

Have you tried connecting it to other people's computers?  If you know someone with WinXP, try connecting it to that and see if the results are any different.

---

### Post by jonnyboysmithy on 2012-04-29
It works on the two winxp machines we have here and on the other windows7 machine (for some reason it DOES work now).
I tried both the usb 3.0 and the usb 2.0 port, still no go.
Anything else I can try?
Why is it spitting out those errors? I would expect it to just work like any other memory stick.

---

### Post by SeijiSensei on 2012-04-29
I would, too. Unfortunately my experience with my LG and a more recent Samsung cell phone indicate that not all USB mass storage devices work with Linux.  Perhaps there's something vaguely proprietary about the interfaces they use.  Here's a [similar bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998") about a Sansa device.  

Did you ever try connecting it to a Mac?  If so, how did that go?

All I can suggest is burning a 12.04 CD, booting from it and choosing "Try Ubuntu".  See if it works with the newer version.  If not, I'd file a bug report at Launchpad with the transcript from dmesg.

---

### Post by jonnyboysmithy on 2012-04-29
Right now I'm using 12.04 as my default.
No I haven't a mac around, nor tried it.
Would you like to report the bug?

---

### Post by SeijiSensei on 2012-04-29
Not really. I don't have the device so I couldn't be able to provide any additional information should one of the developers ask for it.

You can follow the instructions [here]("https://help.ubuntu.com/community/ReportingBugs").  It looks like you should be reporting the problem against the "usb-storage" package given the other bug I linked to above.

---

### Post by jonnyboysmithy on 2012-04-29
Ok, I'll look into it later and report the bug.
Right now I have other things to attend to.

---

### Post by jonnyboysmithy on 2012-04-30
Apparently there is no package called usb-storage. 
Ideas?
Just noticed my computer won't get past the bios when the mp4 player is plugged in to the usb 2.0 port (its not even posting). It just hangs. Curious.

---

### Post by SeijiSensei on 2012-04-30
> **jonnyboysmithy said:**
> Apparently there is no package called usb-storage. 
Ideas?

Sorry.  I misread the other [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998).  The package in question is called simply "linux".

> Just noticed my computer won't get past the bios when the mp4 player is plugged in to the usb 2.0 port (its not even posting). It just hangs. Curious.

Indeed.  Doesn't sound like a very well-engineered device to me.

---

### Post by jonnyboysmithy on 2012-04-30
> **SeijiSensei said:**
> Sorry.  I misread the other [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998").  The package in question is called simply "linux".



Indeed.  Doesn't sound like a very well-engineered device to me.

I would say so ;):-k

---

### Post by jonnyboysmithy on 2012-04-30
Got the bug up there:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991822)

---

### Post by avacado on 2012-06-05
There is hope ;).
I found a fedora workaround at 
[http://us.generation-nt.com/answer/usb-storage-quirk-help-206256222.html](http://us.generation-nt.com/answer/usb-storage-quirk-help-206256222.html)
I do not understad whether this will work on ubuntu but I bought a DSE A807 in an unguarded moment and I have a spare PC.
I am willing to do the testing.
Does anybody know what the instructions mean at the link - how do I 
"add kernel command line parameter"

---

### Post by redcliffs on 2012-07-01
I had this same problem with a DSE 8GB MP3 Player model A8706.  That is, when inserted the drive was not mounted.

I followed the instructions as given in the [http://us.generation-nt.com](http://us.generation-nt.com) website - see above post.  This is what I did.
1) Edit /etc/default/grub (using sudo) so that the grub command line parameters are:
GRUB_CMDLINE_LINUX_DEFAULT="....existing options... usb-storage.quirks=1e74:4641:w"
2) Then I ran update-grub and rebooted.
3) I reset the MP3 player by putting a paper clip into the reset slot.
4) Then plugged it in when the PC rebooted.  It was now recognised by Nautilis and mounted, so I could drag and drop files to it.  However it was not recognised by Rhythmbox.
5) Then I added an empty file to the root directory of the player .is_audio_player and after that rhythmbox recognised it.

Hope that helps anyone else out there with the same problem.  I'm a bit of a newbie so hope the instructions are clear enough.

Cheers,
Rachel

---

### Post by jonnyboysmithy on 2012-07-02
Ok, thanks for that. I'll look into it.
I also found that for the device to work on windows (probably the same with linux) it had to be powered off. Otherwise windows would report it as malfunctioning.

---

