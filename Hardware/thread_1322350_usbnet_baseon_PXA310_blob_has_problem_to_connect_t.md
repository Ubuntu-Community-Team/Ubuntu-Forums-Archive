---
title: "usbnet baseon PXA310 blob has problem to connect to ubuntu8.04"
date: 2009-11-10
forum: Hardware
---

### Post by Newwind on 2009-11-10
Dear all, I have a problem to connect the usbnet device on PXA310 blob. It's hard for ubuntu to detect it. ubuntu can detect this device 1 time, if I plug it to PC 20 times. But it can be detected everytime on WINXP. Below is the dmesg log, the lines in red indicates that ubuntu detected my device 1 time:

[ 5794.650787] usb 5-3: new high speed USB device using ehci_hcd and address 3
[ 5795.133941] usb 5-3: new high speed USB device using ehci_hcd and address 5
[ 5795.433420] usb 5-3: new high speed USB device using ehci_hcd and address 6
[ 5797.226304] usb 5-3: new high speed USB device using ehci_hcd and address 7
[ 5797.525777] usb 5-3: new high speed USB device using ehci_hcd and address 8
[ 5797.825256] usb 5-3: new high speed USB device using ehci_hcd and address 9
[ 5804.130285] usb 5-3: new high speed USB device using ehci_hcd and address 12
[ 5805.102095] usb 5-3: new high speed USB device using ehci_hcd and address 13
[ 5805.212423] usb 5-3: device descriptor read/64, error -71
[ 5805.428026] usb 5-3: device descriptor read/64, error -71
[ 5805.643657] usb 5-3: new high speed USB device using ehci_hcd and address 14
[ 5806.590010] usb 5-3: new high speed USB device using ehci_hcd and address 15
[ 5806.930911] usb 5-3: new high speed USB device using ehci_hcd and address 16
[ 5807.045211] usb 5-3: device descriptor read/64, error -71
[ 5807.260841] usb 5-3: device descriptor read/64, error -71
[ 5807.476461] usb 5-3: new high speed USB device using ehci_hcd and address 17
[ 5807.588275] usb 5-3: device descriptor read/64, error -71
[ 5807.803891] usb 5-3: device descriptor read/64, error -71
[ 5808.019517] usb 5-3: new high speed USB device using ehci_hcd and address 18
[ 5808.428303] usb 5-3: device not accepting address 18, error -71
[ 5808.538892] usb 5-3: new high speed USB device using ehci_hcd and address 19
[ 5808.945903] usb 5-3: device not accepting address 19, error -71
[ 5809.809899] usb 5-3: new high speed USB device using ehci_hcd and address 20
[ 5809.920216] usb 5-3: device descriptor read/64, error -71
[ 5810.137330] usb 5-3: device descriptor read/64, error -71
[ 5810.297933] ehci_hcd 0000:00:1d.7: port 3 reset error -110
[ 5810.297942] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 5819.112210] usb 5-3: new high speed USB device using ehci_hcd and address 22
[ 5819.224020] usb 5-3: device descriptor read/64, error -71
[ 5819.443637] usb 5-3: device descriptor read/64, error -71
[ 5819.659264] usb 5-3: new high speed USB device using ehci_hcd and address 23
[ 5819.771064] usb 5-3: device descriptor read/64, error -71
[ 5819.987185] usb 5-3: device descriptor read/64, error -71
[ 5820.202310] usb 5-3: new high speed USB device using ehci_hcd and address 24
[ 5820.610602] usb 5-3: device not accepting address 24, error -71
[ 5820.721408] usb 5-3: new high speed USB device using ehci_hcd and address 25
[ 5821.128700] usb 5-3: device not accepting address 25, error -71
[ 5994.483012] usb 5-3: new high speed USB device using ehci_hcd and address 27
[ 5995.804705] usb 5-3: new high speed USB device using ehci_hcd and address 32
[ 5996.291856] usb 5-3: new high speed USB device using ehci_hcd and address 34
[ 6003.231781] usb 5-3: new high speed USB device using ehci_hcd and address 36
[ 6003.532753] usb 5-3: new high speed USB device using ehci_hcd and address 37
[ 6003.830740] usb 5-3: new high speed USB device using ehci_hcd and address 38
[ 6020.905022] usb 5-3: new high speed USB device using ehci_hcd and address 40
[ 6867.880081] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 6868.103827] usb 2-1: configuration #1 chosen from 1 choice
[ 6869.968391] usb 2-1: USB disconnect, address 2
[ 6870.208695] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 6870.786935] usb 2-1: device not accepting address 3, error -71
[ 6871.322513] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 6871.544887] usb 2-1: configuration #1 chosen from 1 choice
[ 6872.444101] usb 2-1: USB disconnect, address 5
[ 6877.635528] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 6877.853824] usb 2-1: configuration #1 chosen from 1 choice
[ 6879.379064] usb 2-1: USB disconnect, address 6
[ 6881.247744] usb 2-1: new full speed USB device using uhci_hcd and address 7
[ 6881.474744] usb 2-1: configuration #1 chosen from 1 choice
[ 6881.604155] usb 2-1: USB disconnect, address 7
[ 6882.337846] usb 2-1: new full speed USB device using uhci_hcd and address 8
[ 6882.556874] usb 2-1: configuration #1 chosen from 1 choice
[ 6882.854505] usb 2-1: USB disconnect, address 8
[ 6894.221181] usb 2-1: new full speed USB device using uhci_hcd and address 9
[ 6894.440528] usb 2-1: configuration #1 chosen from 1 choice
[ 6895.716092] usb 2-1: USB disconnect, address 9
[ 6898.052016] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 6898.274164] usb 1-1: configuration #1 chosen from 1 choice
[ 6913.292489] usb 1-1: USB disconnect, address 2
[ 6914.557822] usb 2-1: new full speed USB device using uhci_hcd and address 10
[ 6914.777008] usb 2-1: configuration #1 chosen from 1 choice
[ 6918.988064] usb 2-1: USB disconnect, address 10
[COLOR=Red][ 7268.207312] usb 5-3: new high speed USB device using ehci_hcd and address 52
[ 7268.340041] usb 5-3: configuration #1 chosen from 1 choice
[ 7268.395260] usb0: register 'cdc_subset' at usb-0000:00:1d.7-3, Boot Loader OBject, f2:93:ba:b8:02:a4
[ 7268.395276] usbcore: registered new interface driver cdc_subset
[ 7309.657265] usb 5-3: USB disconnect, address 52
[ 7309.657391] usb0: unregister 'cdc_subset' usb-0000:00:1d.7-3, Boot Loader OBject[/COLOR]
[ 7309.943023] usb 5-3: new high speed USB device using ehci_hcd and address 53
[ 7310.054917] usb 5-3: device descriptor read/64, error -71
[ 7310.270153] usb 5-3: device descriptor read/64, error -71
[ 7310.485717] usb 5-3: new high speed USB device using ehci_hcd and address 54
[ 7310.597530] usb 5-3: device descriptor read/64, error -71
[ 7310.814418] usb 5-3: device descriptor read/64, error -71
[ 7311.027908] usb 5-3: new high speed USB device using ehci_hcd and address 55
[ 7311.163648] usb 5-3: device descriptor read/8, error -71
[ 7311.295673] usb 5-3: device descriptor read/8, error -71
[ 7311.510970] usb 5-3: new high speed USB device using ehci_hcd and address 56
[ 7311.531886] usb 5-3: device descriptor read/8, error -71
[ 7311.655543] usb 5-3: device descriptor read/8, error -71
[ 7391.161314] usb 5-3: new high speed USB device using ehci_hcd and address 57
[ 7391.273619] usb 5-3: device descriptor read/64, error -71
[ 7391.487747] usb 5-3: device descriptor read/64, error -71
[ 7391.703508] usb 5-3: new high speed USB device using ehci_hcd and address 58
[ 7391.815192] usb 5-3: device descriptor read/64, error -71
[ 7392.031801] usb 5-3: device descriptor read/64, error -71
[ 7392.247927] usb 5-3: new high speed USB device using ehci_hcd and address 59
[ 7392.475187] usb 5-3: device descriptor read/8, error -71
[ 7392.599605] usb 5-3: device descriptor read/8, error -71
[ 7392.813943] usb 5-3: new high speed USB device using ehci_hcd and address 60
[ 7392.837319] usb 5-3: device descriptor read/8, error -71
[ 7392.954743] usb 5-3: device descriptor read/8, error -71
[ 7403.632280] usb 5-3: new high speed USB device using ehci_hcd and address 61
[ 7403.747466] usb 5-3: device descriptor read/64, error -71
[ 7403.963051] usb 5-3: device descriptor read/64, error -71
[ 7404.177667] usb 5-3: new high speed USB device using ehci_hcd and address 62
[ 7404.290666] usb 5-3: device descriptor read/64, error -71
[ 7404.505107] usb 5-3: device descriptor read/64, error -71
[ 7404.722217] usb 5-3: new high speed USB device using ehci_hcd and address 63
[ 7404.743771] usb 5-3: device descriptor read/8, error -71
[ 7404.863314] usb 5-3: device descriptor read/8, error -71
[ 7405.077107] usb 5-3: new high speed USB device using ehci_hcd and address 64
[ 7405.483412] usb 5-3: device not accepting address 64, error -71
[ 7405.722994] usb 5-3: new high speed USB device using ehci_hcd and address 65
[ 7405.836276] usb 5-3: device descriptor read/64, error -71
[ 7406.051414] usb 5-3: device descriptor read/64, error -71
[ 7406.461689] usb 5-3: new high speed USB device using ehci_hcd and address 67
[ 7406.573494] usb 5-3: device descriptor read/64, error -71
[ 7445.969926] usb 5-3: new high speed USB device using ehci_hcd and address 68
[ 7460.639552] usb 5-3: new high speed USB device using ehci_hcd and address 69
[ 7477.877400] usb 5-3: new high speed USB device using ehci_hcd and address 70
[ 7503.134941] usb 5-3: new high speed USB device using ehci_hcd and address 71
[ 7503.432937] usb 5-3: new high speed USB device using ehci_hcd and address 72
[ 7503.545243] usb 5-3: device descriptor read/64, error -71
[ 7503.760867] usb 5-3: device descriptor read/64, error -71
[ 7503.979970] usb 5-3: new high speed USB device using ehci_hcd and address 73
[ 7504.095922] usb 5-3: device descriptor read/64, error -71
[ 7504.315905] usb 5-3: device descriptor read/64, error -71
[ 7504.967656] usb 5-3: new high speed USB device using ehci_hcd and address 75
[ 7506.052364] usb 5-3: new high speed USB device using ehci_hcd and address 76
[ 7506.528550] usb 5-3: new high speed USB device using ehci_hcd and address 77
[ 7506.640351] usb 5-3: device descriptor read/64, error -71
[ 7506.854970] usb 5-3: device descriptor read/64, error -71
[ 7507.070589] usb 5-3: new high speed USB device using ehci_hcd and address 78
[ 7507.182431] usb 5-3: device descriptor read/64, error -71
[ 7507.399889] usb 5-3: device descriptor read/64, error -71
[ 7507.614652] usb 5-3: new high speed USB device using ehci_hcd and address 79
[ 7507.636446] usb 5-3: device descriptor read/8, error -71
[ 7507.757068] usb 5-3: device descriptor read/8, error -71
[ 7508.161110] usb 5-3: new high speed USB device using ehci_hcd and address 81
[ 7508.272583] usb 5-3: device descriptor read/64, error -71
[ 7508.496111] usb 5-3: device descriptor read/64, error -71
[ 7508.708313] usb 5-3: new high speed USB device using ehci_hcd and address 82
[ 7509.024192] usb 5-3: new high speed USB device using ehci_hcd and address 83
[ 7509.139505] usb 5-3: device descriptor read/64, error -71
[ 7509.350624] usb 5-3: device descriptor read/64, error -71
[ 7516.334989] usb 5-3: new high speed USB device using ehci_hcd and address 85
[ 7516.447289] usb 5-3: device descriptor read/64, error -71
[ 7516.663394] usb 5-3: device descriptor read/64, error -71
[ 7516.878527] usb 5-3: new high speed USB device using ehci_hcd and address 86
[ 7516.990839] usb 5-3: device descriptor read/64, error -71
[ 7517.204983] usb 5-3: device descriptor read/64, error -71
[ 7517.420653] usb 5-3: new high speed USB device using ehci_hcd and address 87
[ 7517.829524] usb 5-3: device not accepting address 87, error -71
[ 7517.940267] usb 5-3: new high speed USB device using ehci_hcd and address 88
[ 7518.348130] usb 5-3: device not accepting address 88, error -71
[ 7522.804207] usb 5-3: new high speed USB device using ehci_hcd and address 89
[ 7523.167078] usb 5-3: new high speed USB device using ehci_hcd and address 90
[ 7525.691196] usb 5-3: new high speed USB device using ehci_hcd and address 91
[ 7525.823315] usb 5-3: configuration #1 chosen from 1 choice
[ 7525.823477] usb 5-3: can't set config #1, error -71
[ 7531.859096] usb 5-3: USB disconnect, address 91
[ 7532.288253] usb 5-3: new high speed USB device using ehci_hcd and address 92
[ 7533.051028] usb 5-3: new high speed USB device using ehci_hcd and address 93
[ 7534.428605] usb 5-3: new high speed USB device using ehci_hcd and address 94
[ 7534.540292] usb 5-3: device descriptor read/64, error -71
[ 7534.776045] usb 5-3: unable to read config index 0 descriptor/start: -71
[ 7534.776050] usb 5-3: chopping to 0 config(s)
[ 7534.776134] usb 5-3: no configuration chosen from 0 choices
[ 7535.043613] usb 5-3: USB disconnect, address 94
[ 7535.314937] usb 5-3: new high speed USB device using ehci_hcd and address 95
[ 7535.425249] usb 5-3: device descriptor read/64, error -71
[ 7535.641369] usb 5-3: device descriptor read/64, error -71
[ 7535.856552] usb 5-3: new high speed USB device using ehci_hcd and address 96
[ 7535.968298] usb 5-3: device descriptor read/64, error -71
[ 7536.188031] usb 5-3: device descriptor read/64, error -71
[ 7536.404205] usb 5-3: new high speed USB device using ehci_hcd and address 97
[ 7536.811325] usb 5-3: device not accepting address 97, error -71
[ 7536.923174] usb 5-3: new high speed USB device using ehci_hcd and address 98
[ 7537.334435] usb 5-3: device not accepting address 98, error -71
[ 7540.656144] usb 5-3: new high speed USB device using ehci_hcd and address 99
[ 7543.000209] usb 5-3: new high speed USB device using ehci_hcd and address 100
[ 7543.708329] usb 5-3: new high speed USB device using ehci_hcd and address 101
[ 7585.882434] usb 5-3: new high speed USB device using ehci_hcd and address 102
[ 7586.180945] usb 5-3: new high speed USB device using ehci_hcd and address 103
[ 7586.293717] usb 5-3: device descriptor read/64, error -71

---

