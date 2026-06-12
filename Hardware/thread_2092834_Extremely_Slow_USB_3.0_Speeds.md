---
title: "Extremely Slow USB 3.0 Speeds"
date: 2012-12-09
forum: Hardware
---

### Post by MethylTryp on 2012-12-09
I'm occasionally pulling down as low as 10-12MBps, with 25-30 if I'm lucky. dmesg comes up with this: 

[64171.274611] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[64171.287078] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.

I'm not sure it means anything, but I'd really like to figure this one out.

Total newbie by the way.

Here's the entirety of the USB section in dmesg:

```

[52542.246597] usb 9-1: new SuperSpeed USB device number 3 using xhci_hcd
[52542.259499] usb 9-1: Parent hub missing LPM exit latency info.  Power management will be impacted.
[52542.260198] usb 9-1: New USB device found, idVendor=0bc2, idProduct=5031
[52542.260209] usb 9-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[52542.260218] usb 9-1: Product: FreeAgent GoFlex
[52542.260226] usb 9-1: Manufacturer: Seagate
[52542.260234] usb 9-1: SerialNumber: NA0BFJEA
[52542.262124] scsi8 : usb-storage 9-1:1.0
[52543.260833] scsi 8:0:0:0: Direct-Access     Seagate  FreeAgent GoFlex  210 PQ: 0 ANSI: 0
[52543.263452] sd 8:0:0:0: Attached scsi generic sg3 type 0
[52543.264272] sd 8:0:0:0: [sdd] 2930277167 512-byte logical blocks: (1.50 TB/1.36 TiB)
[52543.264751] sd 8:0:0:0: [sdd] Write Protect is off
[52543.264763] sd 8:0:0:0: [sdd] Mode Sense: 0f 00 00 00
[52543.265232] sd 8:0:0:0: [sdd] No Caching mode page present
[52543.265378] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[52543.270022] sd 8:0:0:0: [sdd] No Caching mode page present
[52543.270166] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[52543.307653]  sdd: sdd1
[52543.309557] sd 8:0:0:0: [sdd] No Caching mode page present
[52543.309698] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[52543.309834] sd 8:0:0:0: [sdd] Attached SCSI disk
[55450.024914] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[55450.037415] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[55450.037672] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[55450.037690] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[55601.071076] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[55601.083489] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[55601.083689] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[55601.083700] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[55611.199491] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[55611.211963] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[55611.212181] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[55611.212192] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[55737.076662] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[55737.089092] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[55737.089306] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[55737.089318] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[55747.205077] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[55747.217545] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[55747.217753] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[55747.217764] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[56047.073505] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[56047.085965] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[56047.086187] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[56047.086198] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[56057.201930] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[56057.214418] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[56057.214625] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[56057.214636] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[56125.124784] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[56125.137238] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[56125.137454] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[56125.137465] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[56135.253208] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[56135.265645] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[56135.265852] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[56135.265863] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[56620.057148] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[56620.069586] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[56620.069801] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[56620.069812] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57161.102844] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57161.115310] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57161.115518] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57161.115529] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57247.090347] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57247.102778] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57247.102991] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57247.103002] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57257.218752] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57257.231234] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57257.231446] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57257.231457] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57700.116157] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57700.132516] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57700.132736] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57700.132747] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57742.149602] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57742.162080] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57742.162303] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57742.162314] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57752.277987] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57752.290444] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57752.290651] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57752.290663] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[57982.126663] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[57982.139138] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[57982.139346] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[57982.139357] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[58901.170670] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[58901.183142] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[58901.183355] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[58901.183366] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[59405.191157] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[59405.203607] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[59405.203817] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[59405.203828] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[59467.209742] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[59467.222342] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[59467.222544] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[59467.222555] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[59847.187582] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[59847.200007] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[59847.200223] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[59847.200234] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[59954.197981] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[59954.210427] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[59954.210637] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[59954.210648] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[61670.267270] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[61670.279723] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[61670.279935] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[61670.279947] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[61680.395448] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[61680.407940] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[61680.408148] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[61680.408160] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[61851.262670] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[61851.275125] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[61851.275336] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[61851.275346] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[61909.247774] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[61909.260253] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[61909.260452] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[61909.260464] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[62262.278933] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[62262.291408] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[62262.291635] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[62262.291645] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[62423.258391] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[62423.270826] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[62423.271041] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[62423.271052] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[62587.277987] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[62587.290436] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[62587.290641] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[62587.290652] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[62635.279066] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[62635.291520] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[62635.291736] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[62635.291746] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[62902.293217] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[62902.305662] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[62902.305876] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[62902.305887] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[62955.286469] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[62955.298943] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[62955.299158] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[62955.299169] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[63186.332060] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[63186.344491] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[63186.344716] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[63186.344727] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[63595.302328] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[63595.314791] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[63595.314997] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[63595.315008] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[64072.362637] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[64072.375077] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[64072.375280] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[64072.375291] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[64171.274611] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[64171.287078] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[64171.287285] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[64171.287296] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[64181.402622] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[64181.415103] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[64181.415320] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[64181.415331] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[64355.306931] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[64355.319369] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[64355.319586] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[64355.319604] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[65187.306917] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[65187.319374] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[65187.319596] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[65187.319606] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[65327.400453] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[65327.412943] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[65327.413156] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[65327.413168] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[65478.310660] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[65478.323096] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[65478.323302] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[65478.323313] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[66186.285547] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[66186.298014] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[66186.298217] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[66186.298227] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[66228.302296] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[66228.314761] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[66228.314975] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[66228.314986] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[66456.306470] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[66456.318941] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[66456.319153] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[66456.319164] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[66696.375253] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[66696.387692] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[66696.387882] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[66696.387888] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[66817.337760] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[66817.350201] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[66817.350402] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[66817.350413] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[66884.411215] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[66884.423708] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[66884.423925] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[66884.423937] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[67310.340697] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[67310.357683] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[67310.357917] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[67310.357935] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[67631.308106] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[67631.320902] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[67631.321167] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[67631.321187] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[68180.378876] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[68180.391595] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[68180.391806] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[68180.391816] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[68449.378069] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[68449.390499] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[68449.390712] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[68449.390723] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[68674.344645] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[68674.357074] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[68674.357284] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[68674.357295] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[68684.472920] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[68684.485398] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[68684.485614] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[68684.485624] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[68742.378620] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[68742.391099] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[68742.391312] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[68742.391323] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[68829.421174] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[68829.433600] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[68829.433811] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[68829.433822] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[69659.396503] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[69659.408909] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[69659.409118] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[69659.409130] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[70073.391774] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[70073.404231] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[70073.404432] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[70073.404444] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[70494.427331] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[70494.443662] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[70494.443875] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[70494.443887] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[70728.417999] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[70728.430453] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[70728.430656] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[70728.430667] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[70833.413173] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[70833.425592] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[70833.425778] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[70833.425784] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[70843.541540] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[70843.553993] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[70843.554212] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[70843.554224] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71208.432308] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71208.444795] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71208.445013] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71208.445025] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71218.560636] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71218.573074] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71218.573283] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71218.573294] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71436.470908] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71436.483425] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71436.483647] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71436.483658] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71446.599219] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71446.611642] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71446.611852] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71446.611863] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71649.437037] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71649.449504] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71649.449714] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71649.449725] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71659.565356] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71659.577808] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71659.578019] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71659.578030] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[71785.472916] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[71785.485432] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[71785.485649] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[71785.485660] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[72817.469809] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[72817.482393] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[72817.482746] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[72817.482758] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[72827.598106] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[72827.610547] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[72827.610754] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[72827.610765] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[72938.465166] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[72938.477631] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[72938.477840] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[72938.477851] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[73349.483723] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[73349.496185] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[73349.496399] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[73349.496410] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[74069.502509] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[74069.514977] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[74069.515188] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[74069.515198] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[74079.630793] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[74079.643215] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[74079.643427] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[74079.643439] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[74607.500807] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[74607.513205] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[74607.513435] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[74607.513446] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[74617.629051] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[74617.641549] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[74617.641758] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[74617.641769] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[74706.511411] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[74706.523895] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[74706.524109] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[74706.524120] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[74792.593702] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[74792.606174] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[74792.606392] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[74792.606403] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc
[75183.515537] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[75183.527971] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[75183.528184] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2a0
[75183.528195] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep f6ffa2cc

```

---

