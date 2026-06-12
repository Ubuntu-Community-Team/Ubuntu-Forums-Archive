---
title: "Problems Installing Orange Box"
date: 2008-11-12
forum: General Help
---

### Post by YaroMan86 on 2008-11-12
I run the installer for the Orange Box in WINE as usual, everything proceeds up to the actual installation of the games, when everything seems to freeze up. After restarting X, I ran the terminal and ran a dmesg, this is what I got:

```

[  273.144312] ata1.00: cmd 25/00:00:ef:66:7d/00:01:11:00:00/e0 tag 0 dma 131072 in
[  273.144315]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  273.144321] ata1.00: status: { DRDY ERR }
[  273.144325] ata1.00: error: { UNC }
[  273.264200] ata1.00: configured for UDMA/133
[  273.264236] ata1: EH complete
[  276.084697] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  276.084766] ata1.00: BMDMA stat 0x24
[  276.084827] ata1.00: cmd 25/00:00:ef:66:7d/00:01:11:00:00/e0 tag 0 dma 131072 in
[  276.084830]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  276.084944] ata1.00: status: { DRDY ERR }
[  276.084998] ata1.00: error: { UNC }
[  276.192532] ata1.00: configured for UDMA/133
[  276.192556] ata1: EH complete
[  279.000074] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  279.000089] ata1.00: BMDMA stat 0x24
[  279.000100] ata1.00: cmd 25/00:00:ef:66:7d/00:01:11:00:00/e0 tag 0 dma 131072 in
[  279.000103]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  279.000109] ata1.00: status: { DRDY ERR }
[  279.000113] ata1.00: error: { UNC }
[  279.116515] ata1.00: configured for UDMA/133
[  279.116548] ata1: EH complete
[  281.957227] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  281.957241] ata1.00: BMDMA stat 0x24
[  281.957253] ata1.00: cmd 25/00:00:ef:66:7d/00:01:11:00:00/e0 tag 0 dma 131072 in
[  281.957255]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  281.957262] ata1.00: status: { DRDY ERR }
[  281.957265] ata1.00: error: { UNC }
[  282.064527] ata1.00: configured for UDMA/133
[  282.064564] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  282.064571] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  282.064580] Descriptor sense data with sense descriptors (in hex):
[  282.064584]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  282.064598]         11 7d 67 62 
[  282.064604] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  282.064614] end_request: I/O error, dev sda, sector 293431138
[  282.064659] ata1: EH complete
[  282.083695] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  282.089967] sd 0:0:0:0: [sda] Write Protect is off
[  282.089976] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  282.090049] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  282.090118] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  282.090153] sd 0:0:0:0: [sda] Write Protect is off
[  282.090157] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  282.090221] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  284.939030] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  284.939046] ata1.00: BMDMA stat 0x24
[  284.939058] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  284.939060]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  284.939067] ata1.00: status: { DRDY ERR }
[  284.939070] ata1.00: error: { UNC }
[  285.049259] ata1.00: configured for UDMA/133
[  285.049296] ata1: EH complete
[  287.887820] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  287.887835] ata1.00: BMDMA stat 0x24
[  287.887846] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  287.887849]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  287.887855] ata1.00: status: { DRDY ERR }
[  287.887859] ata1.00: error: { UNC }
[  287.996541] ata1.00: configured for UDMA/133
[  287.996575] ata1: EH complete
[  290.869768] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  290.869783] ata1.00: BMDMA stat 0x24
[  290.869794] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  290.869797]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  290.869803] ata1.00: status: { DRDY ERR }
[  290.869807] ata1.00: error: { UNC }
[  291.000873] ata1.00: configured for UDMA/133
[  291.000906] ata1: EH complete
[  293.826964] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  293.826979] ata1.00: BMDMA stat 0x24
[  293.826990] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  293.826993]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  293.826999] ata1.00: status: { DRDY ERR }
[  293.827002] ata1.00: error: { UNC }
[  293.936508] ata1.00: configured for UDMA/133
[  293.936541] ata1: EH complete
[  296.775579] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  296.775594] ata1.00: BMDMA stat 0x24
[  296.775604] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  296.775607]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  296.775613] ata1.00: status: { DRDY ERR }
[  296.775617] ata1.00: error: { UNC }
[  296.884524] ata1.00: configured for UDMA/133
[  296.884557] ata1: EH complete
[  299.699394] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  299.699409] ata1.00: BMDMA stat 0x24
[  299.699420] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  299.699423]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  299.699429] ata1.00: status: { DRDY ERR }
[  299.699433] ata1.00: error: { UNC }
[  299.800529] ata1.00: configured for UDMA/133
[  299.800567] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  299.800575] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  299.800584] Descriptor sense data with sense descriptors (in hex):
[  299.800588]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  299.800602]         11 7d 67 62 
[  299.800608] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  299.800618] end_request: I/O error, dev sda, sector 293431138
[  299.800663] ata1: EH complete
[  299.801254] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  299.801734] sd 0:0:0:0: [sda] Write Protect is off
[  299.801740] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  299.802582] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  299.803469] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  299.803872] sd 0:0:0:0: [sda] Write Protect is off
[  299.803877] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  299.814887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  302.639799] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  302.639813] ata1.00: BMDMA stat 0x24
[  302.639824] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  302.639827]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  302.639833] ata1.00: status: { DRDY ERR }
[  302.639837] ata1.00: error: { UNC }
[  302.876536] ata1.00: configured for UDMA/133
[  302.876564] ata1: EH complete
[  305.688439] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  305.688454] ata1.00: BMDMA stat 0x24
[  305.688465] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  305.688468]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  305.688474] ata1.00: status: { DRDY ERR }
[  305.688478] ata1.00: error: { UNC }
[  305.796506] ata1.00: configured for UDMA/133
[  305.796540] ata1: EH complete
[  308.612270] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  308.612284] ata1.00: BMDMA stat 0x24
[  308.612296] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  308.612299]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  308.612305] ata1.00: status: { DRDY ERR }
[  308.612309] ata1.00: error: { UNC }
[  308.728534] ata1.00: configured for UDMA/133
[  308.728569] ata1: EH complete
[  311.569301] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  311.569316] ata1.00: BMDMA stat 0x24
[  311.569327] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  311.569330]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  311.569336] ata1.00: status: { DRDY ERR }
[  311.569340] ata1.00: error: { UNC }
[  311.680591] ata1.00: configured for UDMA/133
[  311.680627] ata1: EH complete
[  314.518068] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  314.518082] ata1.00: BMDMA stat 0x24
[  314.518093] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  314.518096]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  314.518102] ata1.00: status: { DRDY ERR }
[  314.518106] ata1.00: error: { UNC }
[  314.616605] ata1.00: configured for UDMA/133
[  314.616637] ata1: EH complete
[  317.450152] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  317.450166] ata1.00: BMDMA stat 0x24
[  317.450177] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  317.450180]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  317.450186] ata1.00: status: { DRDY ERR }
[  317.450190] ata1.00: error: { UNC }
[  317.560515] ata1.00: configured for UDMA/133
[  317.560552] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  317.560560] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  317.560569] Descriptor sense data with sense descriptors (in hex):
[  317.560573]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  317.560587]         11 7d 67 62 
[  317.560593] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  317.560603] end_request: I/O error, dev sda, sector 293431138
[  317.560646] ata1: EH complete
[  317.581668] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  317.581732] sd 0:0:0:0: [sda] Write Protect is off
[  317.581738] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  317.582815] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  317.582887] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  317.582923] sd 0:0:0:0: [sda] Write Protect is off
[  317.582928] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  317.582991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  320.465496] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  320.465511] ata1.00: BMDMA stat 0x24
[  320.465522] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  320.465525]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  320.465531] ata1.00: status: { DRDY ERR }
[  320.465535] ata1.00: error: { UNC }
[  320.656574] ata1.00: configured for UDMA/133
[  320.656608] ata1: EH complete
[  323.489174] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  323.489188] ata1.00: BMDMA stat 0x24
[  323.489199] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  323.489202]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  323.489208] ata1.00: status: { DRDY ERR }
[  323.489212] ata1.00: error: { UNC }
[  323.588519] ata1.00: configured for UDMA/133
[  323.588553] ata1: EH complete
[  326.412919] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  326.412934] ata1.00: BMDMA stat 0x24
[  326.412945] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  326.412947]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  326.412953] ata1.00: status: { DRDY ERR }
[  326.412957] ata1.00: error: { UNC }
[  326.528527] ata1.00: configured for UDMA/133
[  326.528564] ata1: EH complete
[  329.345037] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  329.345051] ata1.00: BMDMA stat 0x24
[  329.345062] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  329.345065]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  329.345071] ata1.00: status: { DRDY ERR }
[  329.345075] ata1.00: error: { UNC }
[  329.452573] ata1.00: configured for UDMA/133
[  329.452609] ata1: EH complete
[  332.302079] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  332.302094] ata1.00: BMDMA stat 0x24
[  332.302105] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  332.302108]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  332.302114] ata1.00: status: { DRDY ERR }
[  332.302118] ata1.00: error: { UNC }
[  332.400567] ata1.00: configured for UDMA/133
[  332.400603] ata1: EH complete
[  335.242545] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  335.242559] ata1.00: BMDMA stat 0x24
[  335.242571] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  335.242574]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  335.242580] ata1.00: status: { DRDY ERR }
[  335.242584] ata1.00: error: { UNC }
[  335.352577] ata1.00: configured for UDMA/133
[  335.352616] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  335.352623] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  335.352632] Descriptor sense data with sense descriptors (in hex):
[  335.352636]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  335.352650]         11 7d 67 62 
[  335.352656] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  335.352665] end_request: I/O error, dev sda, sector 293431138
[  335.352712] ata1: EH complete
[  335.356105] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  338.174601] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  338.174616] ata1.00: BMDMA stat 0x24
[  338.174627] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  338.174630]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  338.174636] ata1.00: status: { DRDY ERR }
[  338.174640] ata1.00: error: { UNC }
[  338.278710] ata1.00: configured for UDMA/133
[  338.278749] ata1: EH complete
[  341.123346] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  341.123417] ata1.00: BMDMA stat 0x24
[  341.123478] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  341.123481]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  341.123595] ata1.00: status: { DRDY ERR }
[  341.123649] ata1.00: error: { UNC }
[  341.236533] ata1.00: configured for UDMA/133
[  341.236568] ata1: EH complete
[  344.063787] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  344.063868] ata1.00: BMDMA stat 0x24
[  344.063938] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  344.063941]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  344.064109] ata1.00: status: { DRDY ERR }
[  344.064172] ata1.00: error: { UNC }
[  344.168586] ata1.00: configured for UDMA/133
[  344.168622] ata1: EH complete
[  347.023153] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  347.023172] ata1.00: BMDMA stat 0x24
[  347.023184] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  347.023187]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  347.023193] ata1.00: status: { DRDY ERR }
[  347.023197] ata1.00: error: { UNC }
[  347.128556] ata1.00: configured for UDMA/133
[  347.128592] ata1: EH complete
[  349.961239] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  349.961254] ata1.00: BMDMA stat 0x24
[  349.961265] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  349.961268]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  349.961274] ata1.00: status: { DRDY ERR }
[  349.961278] ata1.00: error: { UNC }
[  350.069385] ata1.00: configured for UDMA/133
[  350.069421] ata1: EH complete
[  352.910012] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  352.910027] ata1.00: BMDMA stat 0x24
[  352.910037] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  352.910040]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  352.910046] ata1.00: status: { DRDY ERR }
[  352.910050] ata1.00: error: { UNC }
[  353.048528] ata1.00: configured for UDMA/133
[  353.048565] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  353.048573] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  353.048581] Descriptor sense data with sense descriptors (in hex):
[  353.048585]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  353.048599]         11 7d 67 62 
[  353.048605] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  353.048615] end_request: I/O error, dev sda, sector 293431138
[  353.048658] ata1: EH complete
[  353.048795] sd 0:0:0:0: [sda] Write Protect is off
[  353.048800] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  353.049794] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  353.059676] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  353.061743] sd 0:0:0:0: [sda] Write Protect is off
[  353.061753] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  353.064104] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  356.008685] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  356.008699] ata1.00: BMDMA stat 0x24
[  356.008711] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  356.008714]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  356.008720] ata1.00: status: { DRDY ERR }
[  356.008724] ata1.00: error: { UNC }
[  356.288517] ata1.00: configured for UDMA/133
[  356.288547] ata1: EH complete
[  359.124033] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  359.124046] ata1.00: BMDMA stat 0x24
[  359.124057] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  359.124060]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  359.124066] ata1.00: status: { DRDY ERR }
[  359.124070] ata1.00: error: { UNC }
[  359.240517] ata1.00: configured for UDMA/133
[  359.240550] ata1: EH complete
[  362.089458] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  362.089472] ata1.00: BMDMA stat 0x24
[  362.089483] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  362.089486]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  362.089492] ata1.00: status: { DRDY ERR }
[  362.089496] ata1.00: error: { UNC }
[  362.196518] ata1.00: configured for UDMA/133
[  362.196552] ata1: EH complete
[  365.046464] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  365.046478] ata1.00: BMDMA stat 0x24
[  365.046489] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  365.046492]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  365.046498] ata1.00: status: { DRDY ERR }
[  365.046502] ata1.00: error: { UNC }
[  365.149490] ata1.00: configured for UDMA/133
[  365.149525] ata1: EH complete
[  368.003572] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  368.003586] ata1.00: BMDMA stat 0x24
[  368.003597] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  368.003600]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  368.003605] ata1.00: status: { DRDY ERR }
[  368.003609] ata1.00: error: { UNC }
[  368.112597] ata1.00: configured for UDMA/133
[  368.112633] ata1: EH complete
[  370.943978] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  370.943992] ata1.00: BMDMA stat 0x24
[  370.944003] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  370.944006]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  370.944026] ata1.00: status: { DRDY ERR }
[  370.944030] ata1.00: error: { UNC }
[  371.060570] ata1.00: configured for UDMA/133
[  371.060609] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  371.060616] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  371.060625] Descriptor sense data with sense descriptors (in hex):
[  371.060629]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  371.060643]         11 7d 67 62 
[  371.060649] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  371.060659] end_request: I/O error, dev sda, sector 293431138
[  371.060707] ata1: EH complete
[  371.064557] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  373.925982] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  373.925997] ata1.00: BMDMA stat 0x24
[  373.926008] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  373.926010]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  373.926016] ata1.00: status: { DRDY ERR }
[  373.926020] ata1.00: error: { UNC }
[  374.024517] ata1.00: configured for UDMA/133
[  374.024551] ata1: EH complete
[  376.858126] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  376.858141] ata1.00: BMDMA stat 0x24
[  376.858152] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  376.858155]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  376.858161] ata1.00: status: { DRDY ERR }
[  376.858165] ata1.00: error: { UNC }
[  376.968526] ata1.00: configured for UDMA/133
[  376.968560] ata1: EH complete
[  379.790177] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  379.790257] ata1.00: BMDMA stat 0x24
[  379.790327] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  379.790330]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  379.790482] ata1.00: status: { DRDY ERR }
[  379.790545] ata1.00: error: { UNC }
[  379.900554] ata1.00: configured for UDMA/133
[  379.900588] ata1: EH complete
[  382.747280] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  382.747360] ata1.00: BMDMA stat 0x24
[  382.747431] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  382.747434]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  382.747586] ata1.00: status: { DRDY ERR }
[  382.747651] ata1.00: error: { UNC }
[  382.848626] ata1.00: configured for UDMA/133
[  382.848661] ata1: EH complete
[  385.696201] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  385.696223] ata1.00: BMDMA stat 0x24
[  385.696234] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  385.696237]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  385.696243] ata1.00: status: { DRDY ERR }
[  385.696247] ata1.00: error: { UNC }
[  385.804800] ata1.00: configured for UDMA/133
[  385.804834] ata1: EH complete
[  388.619765] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  388.619782] ata1.00: BMDMA stat 0x24
[  388.619793] ata1.00: cmd 25/00:08:5f:67:7d/00:00:11:00:00/e0 tag 0 dma 4096 in
[  388.619796]          res 51/40:00:62:67:7d/40:00:11:00:00/00 Emask 0x9 (media error)
[  388.619802] ata1.00: status: { DRDY ERR }
[  388.619806] ata1.00: error: { UNC }
[  388.720524] ata1.00: configured for UDMA/133
[  388.720553] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  388.720561] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  388.720569] Descriptor sense data with sense descriptors (in hex):
[  388.720574]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  388.720588]         11 7d 67 62 
[  388.720594] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  388.720604] end_request: I/O error, dev sda, sector 293431138
[  388.720634] ata1: EH complete
[  388.720751] sd 0:0:0:0: [sda] Write Protect is off
[  388.720756] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  388.724042] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  388.743535] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  388.749069] sd 0:0:0:0: [sda] Write Protect is off
[  388.749084] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  388.750078] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I don't think my SATA drive is failing or something would have come up in SMART. Any idea what this problem is or how I can overcome it so I can install OB?

---

### Post by Titan8990 on 2008-11-12
I would try installing it via the Steam client. That worked for me w/ Team Fortress 2.

---

