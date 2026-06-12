---
title: "Failed command: READ DMA"
date: 2014-06-01
forum: Hardware
---

### Post by eclectik on 2014-06-01
Ive upgraded to 14.4 recently and everything seemed to go fine on my headless linux server.

But today we had a power cut and upon rebooting my server I noticed it dodnt come online. So plugging a monitor in to investigate showed the boot log completely spammed with :

[209.780320] ata4.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[209.780364] ata4.00: BMDMA stat 0x26
[209.780386] ata4.00: failed command READ DMA
[209.780415] ata4.00: cmd c8/00:08:30:1e:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[209.786415]              res 51/84:08:30:1e:00/84:00:19:00:00/e0  Emask 0x30 (host bus error:
[209.780490] ata4.00: status {DRDY ERR}
[209.780512] ata4.00: error {ICRC ABRT}

Strangely on a reboot it booted all the way to my samba shares being active and I can also SSH in. But the errors are spamming the local login screen intermittently.
Do you think one of my hard drives are failing. Its worth noting despite it stating ata, both my drives are SATA.

Please advise,
Many thanks,
Nige

_**Edit**_

Running:```
 [COLOR=#000000][FONT=Verdana]dmesg | grep ata4[/FONT][/COLOR]
```

results in:

```
[   78.075342] ata4.00: cmd 25/00:80:38:33:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in[   78.077865] ata4.00: status: { DRDY ERR }
[   78.079137] ata4.00: error: { ICRC ABRT }
[   78.080401] ata4: soft resetting link
[   78.252231] ata4.00: configured for UDMA/33
[   78.252241] ata4: EH complete
[   78.270646] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   78.271928] ata4.00: BMDMA stat 0x26
[   78.273202] ata4.00: failed command: READ DMA EXT
[   78.274461] ata4.00: cmd 25/00:80:b8:33:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   78.276993] ata4.00: status: { DRDY ERR }
[   78.278218] ata4.00: error: { ICRC ABRT }
[   78.279433] ata4: soft resetting link
[   78.448226] ata4.00: configured for UDMA/33
[   78.448234] ata4: EH complete
[   78.458240] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   78.459481] ata4.00: BMDMA stat 0x26
[   78.460710] ata4.00: failed command: READ DMA EXT
[   78.461928] ata4.00: cmd 25/00:80:b8:33:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   78.464402] ata4.00: status: { DRDY ERR }
[   78.465650] ata4.00: error: { ICRC ABRT }
[   78.466864] ata4: soft resetting link
[   78.636229] ata4.00: configured for UDMA/33
[   78.636236] ata4: EH complete
[   78.645755] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   78.645787] ata4.00: BMDMA stat 0x26
[   78.645806] ata4.00: failed command: READ DMA EXT
[   78.645832] ata4.00: cmd 25/00:80:b8:33:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   78.645905] ata4.00: status: { DRDY ERR }
[   78.645924] ata4.00: error: { ICRC ABRT }
[   78.645949] ata4: soft resetting link
[   78.816233] ata4.00: configured for UDMA/33
[   78.816239] ata4: EH complete
[   78.838397] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   78.838435] ata4.00: BMDMA stat 0x26
[   78.838455] ata4.00: failed command: READ DMA EXT
[   78.838482] ata4.00: cmd 25/00:80:38:37:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   78.838555] ata4.00: status: { DRDY ERR }
[   78.838575] ata4.00: error: { ICRC ABRT }
[   78.838600] ata4: soft resetting link
[   79.008237] ata4.00: configured for UDMA/33
[   79.008245] ata4: EH complete
[   79.026343] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   79.026377] ata4.00: BMDMA stat 0x26
[   79.026396] ata4.00: failed command: READ DMA EXT
[   79.026423] ata4.00: cmd 25/00:80:b8:37:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   79.026495] ata4.00: status: { DRDY ERR }
[   79.026515] ata4.00: error: { ICRC ABRT }
[   79.026540] ata4: soft resetting link
[   79.196231] ata4.00: configured for UDMA/33
[   79.196238] ata4: EH complete
[   79.214561] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   79.215840] ata4.00: BMDMA stat 0x26
[   79.217106] ata4.00: failed command: READ DMA EXT
[   79.218355] ata4.00: cmd 25/00:80:38:38:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   79.220851] ata4.00: status: { DRDY ERR }
[   79.222058] ata4.00: error: { ICRC ABRT }
[   79.223255] ata4: soft resetting link
[   79.392231] ata4.00: configured for UDMA/33
[   79.392238] ata4: EH complete
[   79.402350] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   79.403565] ata4.00: BMDMA stat 0x26
[   79.404775] ata4.00: failed command: READ DMA EXT
[   79.405971] ata4.00: cmd 25/00:80:38:38:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   79.408402] ata4.00: status: { DRDY ERR }
[   79.409614] ata4.00: error: { ICRC ABRT }
[   79.410816] ata4: soft resetting link
[   79.580225] ata4.00: configured for UDMA/33
[   79.580232] ata4: EH complete
[   79.589957] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   79.589989] ata4.00: BMDMA stat 0x26
[   79.590009] ata4.00: failed command: READ DMA EXT
[   79.590035] ata4.00: cmd 25/00:80:38:38:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   79.590107] ata4.00: status: { DRDY ERR }
[   79.590127] ata4.00: error: { ICRC ABRT }
[   79.590151] ata4: soft resetting link
[   79.760230] ata4.00: configured for UDMA/33
[   79.760236] ata4: EH complete
[   79.778531] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   79.778565] ata4.00: BMDMA stat 0x26
[   79.778584] ata4.00: failed command: READ DMA EXT
[   79.778611] ata4.00: cmd 25/00:80:b8:38:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   79.778683] ata4.00: status: { DRDY ERR }
[   79.778703] ata4.00: error: { ICRC ABRT }
[   79.778728] ata4: soft resetting link
[   79.948228] ata4.00: configured for UDMA/33
[   79.948235] ata4: EH complete
[   79.966878] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   79.966914] ata4.00: BMDMA stat 0x26
[   79.966933] ata4.00: failed command: READ DMA EXT
[   79.966960] ata4.00: cmd 25/00:80:b8:39:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   79.967033] ata4.00: status: { DRDY ERR }
[   79.967053] ata4.00: error: { ICRC ABRT }
[   79.967078] ata4: soft resetting link
[   80.136235] ata4.00: configured for UDMA/33
[   80.136243] ata4: EH complete
[   80.156288] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   80.157543] ata4.00: BMDMA stat 0x26
[   80.158795] ata4.00: failed command: READ DMA EXT
[   80.160058] ata4.00: cmd 25/00:80:b8:3b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   80.162580] ata4.00: status: { DRDY ERR }
[   80.163849] ata4.00: error: { ICRC ABRT }
[   80.165114] ata4: soft resetting link
[   80.336230] ata4.00: configured for UDMA/33
[   80.336239] ata4: EH complete
[   80.354793] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   80.356078] ata4.00: BMDMA stat 0x26
[   80.357337] ata4.00: failed command: READ DMA EXT
[   80.358590] ata4.00: cmd 25/00:80:b8:3b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   80.361097] ata4.00: status: { DRDY ERR }
[   80.362308] ata4.00: error: { ICRC ABRT }
[   80.363509] ata4: soft resetting link
[   80.532229] ata4.00: configured for UDMA/33
[   80.532237] ata4: EH complete
[   80.544020] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   80.544056] ata4.00: BMDMA stat 0x26
[   80.544076] ata4.00: failed command: READ DMA EXT
[   80.544103] ata4.00: cmd 25/00:80:38:3d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   80.544175] ata4.00: status: { DRDY ERR }
[   80.544195] ata4.00: error: { ICRC ABRT }
[   80.544221] ata4: soft resetting link
[   80.716237] ata4.00: configured for UDMA/33
[   80.716246] ata4: EH complete
[   80.734622] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   80.734660] ata4.00: BMDMA stat 0x26
[   80.734680] ata4.00: failed command: READ DMA EXT
[   80.734707] ata4.00: cmd 25/00:80:b8:40:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   80.734780] ata4.00: status: { DRDY ERR }
[   80.734800] ata4.00: error: { ICRC ABRT }
[   80.734825] ata4: soft resetting link
[   80.904230] ata4.00: configured for UDMA/33
[   80.904239] ata4: EH complete
[   80.923685] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   80.923721] ata4.00: BMDMA stat 0x26
[   80.923741] ata4.00: failed command: READ DMA EXT
[   80.923768] ata4.00: cmd 25/00:80:b8:42:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   80.923841] ata4.00: status: { DRDY ERR }
[   80.923861] ata4.00: error: { ICRC ABRT }
[   80.923886] ata4: soft resetting link
[   81.092230] ata4.00: configured for UDMA/33
[   81.092239] ata4: EH complete
[   81.112531] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   81.113798] ata4.00: BMDMA stat 0x26
[   81.115041] ata4.00: failed command: READ DMA EXT
[   81.116300] ata4.00: cmd 25/00:80:b8:43:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   81.116301] ata4.00: status: { DRDY ERR }
[   81.116304] ata4.00: error: { ICRC ABRT }
[   81.116312] ata4: soft resetting link
[   81.288228] ata4.00: configured for UDMA/33
[   81.288237] ata4: EH complete
[   81.303513] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   81.304795] ata4.00: BMDMA stat 0x26
[   81.306043] ata4.00: failed command: READ DMA EXT
[   81.307282] ata4.00: cmd 25/00:80:b8:45:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   81.309765] ata4.00: status: { DRDY ERR }
[   81.310972] ata4.00: error: { ICRC ABRT }
[   81.312167] ata4: soft resetting link
[   81.484229] ata4.00: configured for UDMA/33
[   81.484238] ata4: EH complete
[   81.501968] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   81.502000] ata4.00: BMDMA stat 0x26
[   81.502020] ata4.00: failed command: READ DMA EXT
[   81.502046] ata4.00: cmd 25/00:80:b8:45:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   81.502118] ata4.00: status: { DRDY ERR }
[   81.502138] ata4.00: error: { ICRC ABRT }
[   81.502163] ata4: soft resetting link
[   81.672229] ata4.00: configured for UDMA/33
[   81.672235] ata4: EH complete
[   81.691189] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   81.691226] ata4.00: BMDMA stat 0x26
[   81.691246] ata4.00: failed command: READ DMA EXT
[   81.691272] ata4.00: cmd 25/00:80:38:47:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   81.691345] ata4.00: status: { DRDY ERR }
[   81.691365] ata4.00: error: { ICRC ABRT }
[   81.691390] ata4: soft resetting link
[   81.860230] ata4.00: configured for UDMA/33
[   81.860238] ata4: EH complete
[   81.881734] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   81.881772] ata4.00: BMDMA stat 0x26
[   81.881792] ata4.00: failed command: READ DMA EXT
[   81.881819] ata4.00: cmd 25/00:80:b8:4a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   81.881891] ata4.00: status: { DRDY ERR }
[   81.881911] ata4.00: error: { ICRC ABRT }
[   81.881937] ata4: soft resetting link
[   82.052227] ata4.00: configured for UDMA/33
[   82.052236] ata4: EH complete
[   82.069343] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   82.070611] ata4.00: BMDMA stat 0x26
[   82.071873] ata4.00: failed command: READ DMA EXT
[   82.073131] ata4.00: cmd 25/00:80:b8:4a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   82.075667] ata4.00: status: { DRDY ERR }
[   82.076940] ata4.00: error: { ICRC ABRT }
[   82.078199] ata4: soft resetting link
[   82.248228] ata4.00: configured for UDMA/33
[   82.248235] ata4: EH complete
[   82.268951] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   82.270236] ata4.00: BMDMA stat 0x26
[   82.271504] ata4.00: failed command: READ DMA EXT
[   82.272776] ata4.00: cmd 25/00:80:b8:4b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   82.275295] ata4.00: status: { DRDY ERR }
[   82.276526] ata4.00: error: { ICRC ABRT }
[   82.277744] ata4: soft resetting link
[   82.448233] ata4.00: configured for UDMA/33
[   82.448241] ata4: EH complete
[   82.468970] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   82.470217] ata4.00: BMDMA stat 0x26
[   82.471439] ata4.00: failed command: READ DMA EXT
[   82.472674] ata4.00: cmd 25/00:80:38:4d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   82.475144] ata4.00: status: { DRDY ERR }
[   82.476389] ata4.00: error: { ICRC ABRT }
[   82.477599] ata4: soft resetting link
[   82.648229] ata4.00: configured for UDMA/33
[   82.648239] ata4: EH complete
[   82.670440] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   82.670479] ata4.00: BMDMA stat 0x26
[   82.670500] ata4.00: failed command: READ DMA EXT
[   82.670527] ata4.00: cmd 25/00:80:38:50:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   82.670599] ata4.00: status: { DRDY ERR }
[   82.670619] ata4.00: error: { ICRC ABRT }
[   82.670646] ata4: soft resetting link
[   82.840230] ata4.00: configured for UDMA/33
[   82.840239] ata4: EH complete
[   82.857524] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   82.857556] ata4.00: BMDMA stat 0x26
[   82.857575] ata4.00: failed command: READ DMA EXT
[   82.857601] ata4.00: cmd 25/00:80:38:50:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   82.857674] ata4.00: status: { DRDY ERR }
[   82.857694] ata4.00: error: { ICRC ABRT }
[   82.857718] ata4: soft resetting link
[   83.028230] ata4.00: configured for UDMA/33
[   83.028237] ata4: EH complete
[   83.047464] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   83.047501] ata4.00: BMDMA stat 0x26
[   83.047521] ata4.00: failed command: READ DMA EXT
[   83.047547] ata4.00: cmd 25/00:80:38:52:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   83.047620] ata4.00: status: { DRDY ERR }
[   83.047640] ata4.00: error: { ICRC ABRT }
[   83.047666] ata4: soft resetting link
[   83.216230] ata4.00: configured for UDMA/33
[   83.216238] ata4: EH complete
[   83.236965] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   83.238251] ata4.00: BMDMA stat 0x26
[   83.239507] ata4.00: failed command: READ DMA EXT
[   83.240771] ata4.00: cmd 25/00:80:b8:52:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   83.243280] ata4.00: status: { DRDY ERR }
[   83.244495] ata4.00: error: { ICRC ABRT }
[   83.245692] ata4: soft resetting link
[   83.416231] ata4.00: configured for UDMA/33
[   83.416239] ata4: EH complete
[   83.436273] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   83.437501] ata4.00: BMDMA stat 0x26
[   83.438701] ata4.00: failed command: READ DMA EXT
[   83.439895] ata4.00: cmd 25/00:80:38:53:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   83.442334] ata4.00: status: { DRDY ERR }
[   83.443545] ata4.00: error: { ICRC ABRT }
[   83.444753] ata4: soft resetting link
[   83.616229] ata4.00: configured for UDMA/33
[   83.616237] ata4: EH complete
[   83.636045] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   83.636082] ata4.00: BMDMA stat 0x26
[   83.636101] ata4.00: failed command: READ DMA EXT
[   83.636128] ata4.00: cmd 25/00:80:38:54:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   83.636200] ata4.00: status: { DRDY ERR }
[   83.636220] ata4.00: error: { ICRC ABRT }
[   83.636245] ata4: soft resetting link
[   83.808235] ata4.00: configured for UDMA/33
[   83.808243] ata4: EH complete
[   83.825513] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   83.825551] ata4.00: BMDMA stat 0x26
[   83.825571] ata4.00: failed command: READ DMA EXT
[   83.825597] ata4.00: cmd 25/00:80:38:56:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   83.825669] ata4.00: status: { DRDY ERR }
[   83.825689] ata4.00: error: { ICRC ABRT }
[   83.825715] ata4: soft resetting link
[   83.996231] ata4.00: configured for UDMA/33
[   83.996240] ata4: EH complete
[   84.014566] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   84.014604] ata4.00: BMDMA stat 0x26
[   84.014624] ata4.00: failed command: READ DMA EXT
[   84.014651] ata4.00: cmd 25/00:80:38:58:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   84.014724] ata4.00: status: { DRDY ERR }
[   84.014744] ata4.00: error: { ICRC ABRT }
[   84.014770] ata4: soft resetting link
[   84.184229] ata4.00: configured for UDMA/33
[   84.184237] ata4: EH complete
[   84.203370] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   84.204633] ata4.00: BMDMA stat 0x26
[   84.205886] ata4.00: failed command: READ DMA EXT
[   84.207133] ata4.00: cmd 25/00:80:b8:59:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   84.209661] ata4.00: status: { DRDY ERR }
[   84.210921] ata4.00: error: { ICRC ABRT }
[   84.212180] ata4: soft resetting link
[   84.384232] ata4.00: configured for UDMA/33
[   84.384241] ata4: EH complete
[   84.403531] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   84.404817] ata4.00: BMDMA stat 0x26
[   84.406072] ata4.00: failed command: READ DMA EXT
[   84.407318] ata4.00: cmd 25/00:80:38:5b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   84.409812] ata4.00: status: { DRDY ERR }
[   84.411016] ata4.00: error: { ICRC ABRT }
[   84.412214] ata4: soft resetting link
[   84.584230] ata4.00: configured for UDMA/33
[   84.584239] ata4: EH complete
[   84.602015] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   84.602047] ata4.00: BMDMA stat 0x26
[   84.602067] ata4.00: failed command: READ DMA EXT
[   84.602093] ata4.00: cmd 25/00:80:38:5b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   84.602165] ata4.00: status: { DRDY ERR }
[   84.602185] ata4.00: error: { ICRC ABRT }
[   84.602210] ata4: soft resetting link
[   84.772228] ata4.00: configured for UDMA/33
[   84.772234] ata4: EH complete
[   84.789907] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   84.789939] ata4.00: BMDMA stat 0x26
[   84.789958] ata4.00: failed command: READ DMA EXT
[   84.789984] ata4.00: cmd 25/00:80:38:5b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   84.790056] ata4.00: status: { DRDY ERR }
[   84.790076] ata4.00: error: { ICRC ABRT }
[   84.790100] ata4: soft resetting link
[   84.960233] ata4.00: configured for UDMA/33
[   84.960239] ata4: EH complete
[   84.978827] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   84.978863] ata4.00: BMDMA stat 0x26
[   84.978883] ata4.00: failed command: READ DMA EXT
[   84.978909] ata4.00: cmd 25/00:80:38:5c:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   84.978981] ata4.00: status: { DRDY ERR }
[   84.979001] ata4.00: error: { ICRC ABRT }
[   84.979026] ata4: soft resetting link
[   85.148227] ata4.00: configured for UDMA/33
[   85.148235] ata4: EH complete
[   85.168473] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   85.169742] ata4.00: BMDMA stat 0x26
[   85.170987] ata4.00: failed command: READ DMA EXT
[   85.172242] ata4.00: cmd 25/00:80:b8:5e:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   85.174750] ata4.00: status: { DRDY ERR }
[   85.176014] ata4.00: error: { ICRC ABRT }
[   85.177263] ata4: soft resetting link
[   85.348228] ata4.00: configured for UDMA/33
[   85.348236] ata4: EH complete
[   85.367287] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   85.368569] ata4.00: BMDMA stat 0x26
[   85.369831] ata4.00: failed command: READ DMA EXT
[   85.371074] ata4.00: cmd 25/00:80:38:5f:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   85.373567] ata4.00: status: { DRDY ERR }
[   85.374777] ata4.00: error: { ICRC ABRT }
[   85.375972] ata4: soft resetting link
[   85.548227] ata4.00: configured for UDMA/33
[   85.548236] ata4: EH complete
[   85.566148] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   85.566181] ata4.00: BMDMA stat 0x26
[   85.566201] ata4.00: failed command: READ DMA EXT
[   85.566227] ata4.00: cmd 25/00:80:38:5f:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   85.566299] ata4.00: status: { DRDY ERR }
[   85.566319] ata4.00: error: { ICRC ABRT }
[   85.566344] ata4: soft resetting link
[   85.736229] ata4.00: configured for UDMA/33
[   85.736235] ata4: EH complete
[   85.753617] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   85.753649] ata4.00: BMDMA stat 0x26
[   85.753668] ata4.00: failed command: READ DMA EXT
[   85.753694] ata4.00: cmd 25/00:80:38:5f:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   85.753766] ata4.00: status: { DRDY ERR }
[   85.753786] ata4.00: error: { ICRC ABRT }
[   85.753810] ata4: soft resetting link
[   85.924233] ata4.00: configured for UDMA/33
[   85.924239] ata4: EH complete
[   85.944628] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   85.944665] ata4.00: BMDMA stat 0x26
[   85.944684] ata4.00: failed command: READ DMA EXT
[   85.944711] ata4.00: cmd 25/00:80:b8:60:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   85.944784] ata4.00: status: { DRDY ERR }
[   85.944804] ata4.00: error: { ICRC ABRT }
[   85.944829] ata4: soft resetting link
[   86.116229] ata4.00: configured for UDMA/33
[   86.116237] ata4: EH complete
[   86.132758] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   86.134029] ata4.00: BMDMA stat 0x26
[   86.135279] ata4.00: failed command: READ DMA EXT
[   86.136536] ata4.00: cmd 25/00:80:38:61:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   86.139054] ata4.00: status: { DRDY ERR }
[   86.140325] ata4.00: error: { ICRC ABRT }
[   86.141582] ata4: soft resetting link
[   86.312227] ata4.00: configured for UDMA/33
[   86.312235] ata4: EH complete
[   86.331551] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   86.332838] ata4.00: BMDMA stat 0x26
[   86.334105] ata4.00: failed command: READ DMA EXT
[   86.335365] ata4.00: cmd 25/00:80:38:61:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   86.337888] ata4.00: status: { DRDY ERR }
[   86.339115] ata4.00: error: { ICRC ABRT }
[   86.340335] ata4: soft resetting link
[   86.512226] ata4.00: configured for UDMA/33
[   86.512233] ata4: EH complete
[   86.533230] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   86.533269] ata4.00: BMDMA stat 0x26
[   86.533289] ata4.00: failed command: READ DMA EXT
[   86.533316] ata4.00: cmd 25/00:80:38:64:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   86.533388] ata4.00: status: { DRDY ERR }
[   86.533408] ata4.00: error: { ICRC ABRT }
[   86.533435] ata4: soft resetting link
[   86.704230] ata4.00: configured for UDMA/33
[   86.704239] ata4: EH complete
[   86.721228] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   86.721264] ata4.00: BMDMA stat 0x26
[   86.721284] ata4.00: failed command: READ DMA EXT
[   86.721310] ata4.00: cmd 25/00:80:38:65:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   86.721383] ata4.00: status: { DRDY ERR }
[   86.721403] ata4.00: error: { ICRC ABRT }
[   86.721428] ata4: soft resetting link
[   86.892227] ata4.00: configured for UDMA/33
[   86.892236] ata4: EH complete
[   86.909920] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   86.909955] ata4.00: BMDMA stat 0x26
[   86.909975] ata4.00: failed command: READ DMA EXT
[   86.910002] ata4.00: cmd 25/00:80:38:66:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   86.910074] ata4.00: status: { DRDY ERR }
[   86.910094] ata4.00: error: { ICRC ABRT }
[   86.910119] ata4: soft resetting link
[   87.080227] ata4.00: configured for UDMA/33
[   87.080235] ata4: EH complete
[   87.098464] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   87.099754] ata4.00: BMDMA stat 0x26
[   87.101037] ata4.00: failed command: READ DMA EXT
[   87.102306] ata4.00: cmd 25/00:80:38:67:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   87.104872] ata4.00: status: { DRDY ERR }
[   87.106157] ata4.00: error: { ICRC ABRT }
[   87.107412] ata4: soft resetting link
[   87.276228] ata4.00: configured for UDMA/33
[   87.276237] ata4: EH complete
[   87.285950] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   87.287225] ata4.00: BMDMA stat 0x26
[   87.288492] ata4.00: failed command: READ DMA EXT
[   87.289747] ata4.00: cmd 25/00:80:38:67:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   87.292252] ata4.00: status: { DRDY ERR }
[   87.293467] ata4.00: error: { ICRC ABRT }
[   87.294665] ata4: soft resetting link
[   87.464230] ata4.00: configured for UDMA/33
[   87.464237] ata4: EH complete
[   87.474757] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   87.475982] ata4.00: BMDMA stat 0x26
[   87.477197] ata4.00: failed command: READ DMA EXT
[   87.478397] ata4.00: cmd 25/00:80:38:68:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   87.480823] ata4.00: status: { DRDY ERR }
[   87.482035] ata4.00: error: { ICRC ABRT }
[   87.483253] ata4: soft resetting link
[   87.652227] ata4.00: configured for UDMA/33
[   87.652236] ata4: EH complete
[   87.662984] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   87.663019] ata4.00: BMDMA stat 0x26
[   87.663039] ata4.00: failed command: READ DMA EXT
[   87.663065] ata4.00: cmd 25/00:80:b8:68:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   87.663138] ata4.00: status: { DRDY ERR }
[   87.663158] ata4.00: error: { ICRC ABRT }
[   87.663183] ata4: soft resetting link
[   87.832230] ata4.00: configured for UDMA/33
[   87.832237] ata4: EH complete
[   87.850973] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   87.851006] ata4.00: BMDMA stat 0x26
[   87.851025] ata4.00: failed command: READ DMA EXT
[   87.851051] ata4.00: cmd 25/00:80:38:69:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   87.851123] ata4.00: status: { DRDY ERR }
[   87.851143] ata4.00: error: { ICRC ABRT }
[   87.851168] ata4: soft resetting link
[   88.020229] ata4.00: configured for UDMA/33
[   88.020236] ata4: EH complete
[   88.038461] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   88.038492] ata4.00: BMDMA stat 0x26
[   88.038511] ata4.00: failed command: READ DMA EXT
[   88.038538] ata4.00: cmd 25/00:80:38:69:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   88.038609] ata4.00: status: { DRDY ERR }
[   88.038629] ata4.00: error: { ICRC ABRT }
[   88.038654] ata4: soft resetting link
[   88.208228] ata4.00: configured for UDMA/33
[   88.208234] ata4: EH complete
[   88.228327] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   88.229581] ata4.00: BMDMA stat 0x26
[   88.230826] ata4.00: failed command: READ DMA EXT
[   88.232077] ata4.00: cmd 25/00:80:38:6b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   88.234564] ata4.00: status: { DRDY ERR }
[   88.235765] ata4.00: error: { ICRC ABRT }
[   88.236959] ata4: soft resetting link
[   88.408231] ata4.00: configured for UDMA/33
[   88.408240] ata4: EH complete
[   88.426667] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   88.427875] ata4.00: BMDMA stat 0x26
[   88.429075] ata4.00: failed command: READ DMA EXT
[   88.430264] ata4.00: cmd 25/00:80:38:6b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   88.432670] ata4.00: status: { DRDY ERR }
[   88.433872] ata4.00: error: { ICRC ABRT }
[   88.435065] ata4: soft resetting link
[   88.604226] ata4.00: configured for UDMA/33
[   88.604233] ata4: EH complete
[   88.615643] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   88.615680] ata4.00: BMDMA stat 0x26
[   88.615700] ata4.00: failed command: READ DMA EXT
[   88.615727] ata4.00: cmd 25/00:80:38:6c:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   88.615799] ata4.00: status: { DRDY ERR }
[   88.615819] ata4.00: error: { ICRC ABRT }
[   88.615845] ata4: soft resetting link
[   88.784228] ata4.00: configured for UDMA/33
[   88.784236] ata4: EH complete
[   88.803064] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   88.803096] ata4.00: BMDMA stat 0x26
[   88.803115] ata4.00: failed command: READ DMA EXT
[   88.803142] ata4.00: cmd 25/00:80:38:6c:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   88.803214] ata4.00: status: { DRDY ERR }
[   88.803234] ata4.00: error: { ICRC ABRT }
[   88.803259] ata4: soft resetting link
[   88.972235] ata4.00: configured for UDMA/33
[   88.972242] ata4: EH complete
[   88.991818] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   88.991854] ata4.00: BMDMA stat 0x26
[   88.991873] ata4.00: failed command: READ DMA EXT
[   88.991900] ata4.00: cmd 25/00:80:38:6d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   88.991973] ata4.00: status: { DRDY ERR }
[   88.991993] ata4.00: error: { ICRC ABRT }
[   88.992026] ata4: soft resetting link
[   89.164231] ata4.00: configured for UDMA/33
[   89.164238] ata4: EH complete
[   89.180492] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   89.181756] ata4.00: BMDMA stat 0x26
[   89.183000] ata4.00: failed command: READ DMA EXT
[   89.184252] ata4.00: cmd 25/00:80:b8:6d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   89.186763] ata4.00: status: { DRDY ERR }
[   89.188026] ata4.00: error: { ICRC ABRT }
[   89.189275] ata4: soft resetting link
[   89.360231] ata4.00: configured for UDMA/33
[   89.360238] ata4: EH complete
[   89.382862] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   89.384150] ata4.00: BMDMA stat 0x26
[   89.385403] ata4.00: failed command: READ DMA EXT
[   89.386654] ata4.00: cmd 25/00:80:b8:70:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   89.389156] ata4.00: status: { DRDY ERR }
[   89.390370] ata4.00: error: { ICRC ABRT }
[   89.391568] ata4: soft resetting link
[   89.560227] ata4.00: configured for UDMA/33
[   89.560237] ata4: EH complete
[   89.572277] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   89.572316] ata4.00: BMDMA stat 0x26
[   89.572336] ata4.00: failed command: READ DMA EXT
[   89.572363] ata4.00: cmd 25/00:80:b8:72:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   89.572435] ata4.00: status: { DRDY ERR }
[   89.572455] ata4.00: error: { ICRC ABRT }
[   89.572480] ata4: soft resetting link
[   89.744228] ata4.00: configured for UDMA/33
[   89.744237] ata4: EH complete
[   89.760236] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   89.760269] ata4.00: BMDMA stat 0x26
[   89.760289] ata4.00: failed command: READ DMA EXT
[   89.760315] ata4.00: cmd 25/00:80:38:73:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   89.760387] ata4.00: status: { DRDY ERR }
[   89.760407] ata4.00: error: { ICRC ABRT }
[   89.760432] ata4: soft resetting link
[   89.932229] ata4.00: configured for UDMA/33
[   89.932236] ata4: EH complete
[   89.948640] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   89.948675] ata4.00: BMDMA stat 0x26
[   89.948694] ata4.00: failed command: READ DMA EXT
[   89.948721] ata4.00: cmd 25/00:80:b8:73:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   89.948793] ata4.00: status: { DRDY ERR }
[   89.948813] ata4.00: error: { ICRC ABRT }
[   89.948838] ata4: soft resetting link
[   90.120230] ata4.00: configured for UDMA/33
[   90.120237] ata4: EH complete
[   90.135936] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   90.137215] ata4.00: BMDMA stat 0x26
[   90.138469] ata4.00: failed command: READ DMA EXT
[   90.139719] ata4.00: cmd 25/00:80:b8:73:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   90.142250] ata4.00: status: { DRDY ERR }
[   90.143518] ata4.00: error: { ICRC ABRT }
[   90.144781] ata4: soft resetting link
[   90.316230] ata4.00: configured for UDMA/33
[   90.316237] ata4: EH complete
[   90.339483] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   90.340782] ata4.00: BMDMA stat 0x26
[   90.342051] ata4.00: failed command: READ DMA EXT
[   90.343312] ata4.00: cmd 25/00:80:38:79:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   90.345837] ata4.00: status: { DRDY ERR }
[   90.347068] ata4.00: error: { ICRC ABRT }
[   90.348292] ata4: soft resetting link
[   90.520232] ata4.00: configured for UDMA/33
[   90.520241] ata4: EH complete
[   90.538997] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   90.539034] ata4.00: BMDMA stat 0x26
[   90.539054] ata4.00: failed command: READ DMA EXT
[   90.539081] ata4.00: cmd 25/00:80:38:7a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   90.539153] ata4.00: status: { DRDY ERR }
[   90.539173] ata4.00: error: { ICRC ABRT }
[   90.539199] ata4: soft resetting link
[   90.708229] ata4.00: configured for UDMA/33
[   90.708236] ata4: EH complete
[   90.727097] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   90.727132] ata4.00: BMDMA stat 0x26
[   90.727151] ata4.00: failed command: READ DMA EXT
[   90.727178] ata4.00: cmd 25/00:80:b8:7a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   90.727250] ata4.00: status: { DRDY ERR }
[   90.727270] ata4.00: error: { ICRC ABRT }
[   90.727295] ata4: soft resetting link
[   90.896230] ata4.00: configured for UDMA/33
[   90.896238] ata4: EH complete
[   90.918550] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   90.918586] ata4.00: BMDMA stat 0x26
[   90.918607] ata4.00: failed command: READ DMA EXT
[   90.918633] ata4.00: cmd 25/00:80:38:7d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   90.918706] ata4.00: status: { DRDY ERR }
[   90.918726] ata4.00: error: { ICRC ABRT }
[   90.918751] ata4: soft resetting link
[   91.088228] ata4.00: configured for UDMA/33
[   91.088236] ata4: EH complete
[   91.107455] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   91.108760] ata4.00: BMDMA stat 0x26
[   91.110034] ata4.00: failed command: READ DMA EXT
[   91.111305] ata4.00: cmd 25/00:80:b8:7e:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   91.113874] ata4.00: status: { DRDY ERR }
[   91.115160] ata4.00: error: { ICRC ABRT }
[   91.116428] ata4: soft resetting link
[   91.288233] ata4.00: configured for UDMA/33
[   91.288241] ata4: EH complete
[   91.307531] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   91.308834] ata4.00: BMDMA stat 0x26
[   91.310094] ata4.00: failed command: READ DMA EXT
[   91.311345] ata4.00: cmd 25/00:80:38:80:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   91.313849] ata4.00: status: { DRDY ERR }
[   91.315064] ata4.00: error: { ICRC ABRT }
[   91.316272] ata4: soft resetting link
[   91.488229] ata4.00: configured for UDMA/33
[   91.488237] ata4: EH complete
[   91.506180] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   91.506213] ata4.00: BMDMA stat 0x26
[   91.506232] ata4.00: failed command: READ DMA EXT
[   91.506258] ata4.00: cmd 25/00:80:38:80:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   91.506331] ata4.00: status: { DRDY ERR }
[   91.506350] ata4.00: error: { ICRC ABRT }
[   91.506375] ata4: soft resetting link
[   91.676228] ata4.00: configured for UDMA/33
[   91.676234] ata4: EH complete
[   91.693899] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   91.693931] ata4.00: BMDMA stat 0x26
[   91.693950] ata4.00: failed command: READ DMA EXT
[   91.693977] ata4.00: cmd 25/00:80:38:80:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   91.694049] ata4.00: status: { DRDY ERR }
[   91.694069] ata4.00: error: { ICRC ABRT }
[   91.694093] ata4: soft resetting link
[   91.864227] ata4.00: configured for UDMA/33
[   91.864233] ata4: EH complete
[   91.882810] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   91.882846] ata4.00: BMDMA stat 0x26
[   91.882865] ata4.00: failed command: READ DMA EXT
[   91.882892] ata4.00: cmd 25/00:80:38:81:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   91.882965] ata4.00: status: { DRDY ERR }
[   91.882984] ata4.00: error: { ICRC ABRT }
[   91.883010] ata4: soft resetting link
[   92.052228] ata4.00: configured for UDMA/33
[   92.052236] ata4: EH complete
[   92.072204] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   92.073456] ata4.00: BMDMA stat 0x26
[   92.074704] ata4.00: failed command: READ DMA EXT
[   92.075949] ata4.00: cmd 25/00:80:38:83:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   92.078478] ata4.00: status: { DRDY ERR }
[   92.079740] ata4.00: error: { ICRC ABRT }
[   92.081006] ata4: soft resetting link
[   92.252229] ata4.00: configured for UDMA/33
[   92.252238] ata4: EH complete
[   92.271633] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   92.272925] ata4.00: BMDMA stat 0x26
[   92.274181] ata4.00: failed command: READ DMA EXT
[   92.275433] ata4.00: cmd 25/00:80:38:84:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   92.277935] ata4.00: status: { DRDY ERR }
[   92.279144] ata4.00: error: { ICRC ABRT }
[   92.280345] ata4: soft resetting link
[   92.452238] ata4.00: configured for UDMA/33
[   92.452246] ata4: EH complete
[   92.470901] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   92.472131] ata4.00: BMDMA stat 0x26
[   92.473340] ata4.00: failed command: READ DMA EXT
[   92.474534] ata4.00: cmd 25/00:80:b8:84:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   92.476953] ata4.00: status: { DRDY ERR }
[   92.478163] ata4.00: error: { ICRC ABRT }
[   92.479364] ata4: soft resetting link
[   92.648230] ata4.00: configured for UDMA/33
[   92.648239] ata4: EH complete
[   92.658390] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   92.658422] ata4.00: BMDMA stat 0x26
[   92.658441] ata4.00: failed command: READ DMA EXT
[   92.658468] ata4.00: cmd 25/00:80:b8:84:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   92.658540] ata4.00: status: { DRDY ERR }
[   92.658560] ata4.00: error: { ICRC ABRT }
[   92.658584] ata4: soft resetting link
[   92.828230] ata4.00: configured for UDMA/33
[   92.828237] ata4: EH complete
[   92.847056] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   92.847092] ata4.00: BMDMA stat 0x26
[   92.847111] ata4.00: failed command: READ DMA EXT
[   92.847138] ata4.00: cmd 25/00:80:b8:85:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   92.847211] ata4.00: status: { DRDY ERR }
[   92.847231] ata4.00: error: { ICRC ABRT }
[   92.847256] ata4: soft resetting link
[   93.016229] ata4.00: configured for UDMA/33
[   93.016236] ata4: EH complete
[   93.034985] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   93.035019] ata4.00: BMDMA stat 0x26
[   93.035038] ata4.00: failed command: READ DMA EXT
[   93.035065] ata4.00: cmd 25/00:80:38:86:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   93.035137] ata4.00: status: { DRDY ERR }
[   93.035157] ata4.00: error: { ICRC ABRT }
[   93.035182] ata4: soft resetting link
[   93.204227] ata4.00: configured for UDMA/33
[   93.204235] ata4: EH complete
[   93.222737] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   93.224014] ata4.00: BMDMA stat 0x26
[   93.225260] ata4.00: failed command: READ DMA EXT
[   93.226501] ata4.00: cmd 25/00:80:38:86:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   93.228988] ata4.00: status: { DRDY ERR }
[   93.230195] ata4.00: error: { ICRC ABRT }
[   93.231387] ata4: soft resetting link
[   93.400227] ata4.00: configured for UDMA/33
[   93.400234] ata4: EH complete
[   93.411182] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   93.412414] ata4.00: BMDMA stat 0x26
[   93.413617] ata4.00: failed command: READ DMA EXT
[   93.414817] ata4.00: cmd 25/00:80:b8:86:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   93.417253] ata4.00: status: { DRDY ERR }
[   93.418464] ata4.00: error: { ICRC ABRT }
[   93.419671] ata4: soft resetting link
[   93.588231] ata4.00: configured for UDMA/33
[   93.588239] ata4: EH complete
[   93.599454] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   93.599491] ata4.00: BMDMA stat 0x26
[   93.599510] ata4.00: failed command: READ DMA EXT
[   93.599537] ata4.00: cmd 25/00:80:b8:87:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   93.599609] ata4.00: status: { DRDY ERR }
[   93.599629] ata4.00: error: { ICRC ABRT }
[   93.599654] ata4: soft resetting link
[   93.768229] ata4.00: configured for UDMA/33
[   93.768237] ata4: EH complete
[   93.786948] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   93.786980] ata4.00: BMDMA stat 0x26
[   93.786999] ata4.00: failed command: READ DMA EXT
[   93.787025] ata4.00: cmd 25/00:80:b8:87:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   93.787097] ata4.00: status: { DRDY ERR }
[   93.787117] ata4.00: error: { ICRC ABRT }
[   93.787142] ata4: soft resetting link
[   93.956227] ata4.00: configured for UDMA/33
[   93.956233] ata4: EH complete
[   93.974838] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   93.974870] ata4.00: BMDMA stat 0x26
[   93.974889] ata4.00: failed command: READ DMA EXT
[   93.974915] ata4.00: cmd 25/00:80:b8:87:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   93.974988] ata4.00: status: { DRDY ERR }
[   93.975007] ata4.00: error: { ICRC ABRT }
[   93.975032] ata4: soft resetting link
[   94.144227] ata4.00: configured for UDMA/33
[   94.144233] ata4: EH complete
[   94.165717] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   94.167007] ata4.00: BMDMA stat 0x26
[   94.168284] ata4.00: failed command: READ DMA EXT
[   94.169549] ata4.00: cmd 25/00:80:b8:8a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   94.172112] ata4.00: status: { DRDY ERR }
[   94.173394] ata4.00: error: { ICRC ABRT }
[   94.174671] ata4: soft resetting link
[   94.344236] ata4.00: configured for UDMA/33
[   94.344245] ata4: EH complete
[   94.366375] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   94.367677] ata4.00: BMDMA stat 0x26
[   94.368975] ata4.00: failed command: READ DMA EXT
[   94.370254] ata4.00: cmd 25/00:80:b8:8b:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   94.372810] ata4.00: status: { DRDY ERR }
[   94.374052] ata4.00: error: { ICRC ABRT }
[   94.375262] ata4: soft resetting link
[   94.544227] ata4.00: configured for UDMA/33
[   94.544236] ata4: EH complete
[   94.554620] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   94.554654] ata4.00: BMDMA stat 0x26
[   94.554674] ata4.00: failed command: READ DMA EXT
[   94.554700] ata4.00: cmd 25/00:80:38:8c:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   94.554773] ata4.00: status: { DRDY ERR }
[   94.554793] ata4.00: error: { ICRC ABRT }
[   94.554818] ata4: soft resetting link
[   94.724231] ata4.00: configured for UDMA/33
[   94.724238] ata4: EH complete
[   94.742135] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   94.742167] ata4.00: BMDMA stat 0x26
[   94.742186] ata4.00: failed command: READ DMA EXT
[   94.742213] ata4.00: cmd 25/00:80:38:8c:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   94.742285] ata4.00: status: { DRDY ERR }
[   94.742305] ata4.00: error: { ICRC ABRT }
[   94.742329] ata4: soft resetting link
[   94.912229] ata4.00: configured for UDMA/33
[   94.912236] ata4: EH complete
[   94.931317] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   94.931352] ata4.00: BMDMA stat 0x26
[   94.931372] ata4.00: failed command: READ DMA EXT
[   94.931398] ata4.00: cmd 25/00:80:38:8d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   94.931471] ata4.00: status: { DRDY ERR }
[   94.931490] ata4.00: error: { ICRC ABRT }
[   94.931515] ata4: soft resetting link
[   95.100229] ata4.00: configured for MWDMA2
[   95.100237] ata4: EH complete
[   95.118474] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   95.119760] ata4.00: BMDMA stat 0x26
[   95.121028] ata4.00: failed command: READ DMA EXT
[   95.122283] ata4.00: cmd 25/00:80:38:8d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   95.124836] ata4.00: status: { DRDY ERR }
[   95.126104] ata4.00: error: { ICRC ABRT }
[   95.127363] ata4: soft resetting link
[   95.296227] ata4.00: configured for MWDMA2
[   95.296233] ata4: EH complete
[   95.307009] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   95.308300] ata4.00: BMDMA stat 0x26
[   95.309566] ata4.00: failed command: READ DMA EXT
[   95.310825] ata4.00: cmd 25/00:80:b8:8d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   95.313350] ata4.00: status: { DRDY ERR }
[   95.314568] ata4.00: error: { ICRC ABRT }
[   95.315774] ata4: soft resetting link
[   95.484743] ata4.00: configured for MWDMA2
[   95.484751] ata4: EH complete
[   95.495441] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   95.495479] ata4.00: BMDMA stat 0x26
[   95.495498] ata4.00: failed command: READ DMA EXT
[   95.495525] ata4.00: cmd 25/00:80:b8:8e:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   95.495597] ata4.00: status: { DRDY ERR }
[   95.495617] ata4.00: error: { ICRC ABRT }
[   95.495643] ata4: soft resetting link
[   95.664229] ata4.00: configured for MWDMA2
[   95.664237] ata4: EH complete
[   95.683568] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   95.683601] ata4.00: BMDMA stat 0x26
[   95.683621] ata4.00: failed command: READ DMA EXT
[   95.683647] ata4.00: cmd 25/00:80:38:8f:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   95.683719] ata4.00: status: { DRDY ERR }
[   95.683739] ata4.00: error: { ICRC ABRT }
[   95.683763] ata4: soft resetting link
[   95.852229] ata4.00: configured for MWDMA2
[   95.852236] ata4: EH complete
[   95.871131] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   95.871163] ata4.00: BMDMA stat 0x26
[   95.871182] ata4.00: failed command: READ DMA EXT
[   95.871209] ata4.00: cmd 25/00:80:38:8f:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   95.871281] ata4.00: status: { DRDY ERR }
[   95.871301] ata4.00: error: { ICRC ABRT }
[   95.871326] ata4: soft resetting link
[   96.040228] ata4.00: configured for MWDMA2
[   96.040235] ata4: EH complete
[   96.061464] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   96.062714] ata4.00: BMDMA stat 0x26
[   96.063963] ata4.00: failed command: READ DMA EXT
[   96.065222] ata4.00: cmd 25/00:80:b8:91:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   96.067735] ata4.00: status: { DRDY ERR }
[   96.069006] ata4.00: error: { ICRC ABRT }
[   96.070260] ata4: soft resetting link
[   96.240231] ata4.00: configured for MWDMA2
[   96.240241] ata4: EH complete
[   96.262789] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   96.264082] ata4.00: BMDMA stat 0x26
[   96.265340] ata4.00: failed command: READ DMA EXT
[   96.266591] ata4.00: cmd 25/00:80:38:95:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   96.269090] ata4.00: status: { DRDY ERR }
[   96.270299] ata4.00: error: { ICRC ABRT }
[   96.271496] ata4: soft resetting link
[   96.440232] ata4.00: configured for MWDMA2
[   96.440241] ata4: EH complete
[   96.451714] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   96.452945] ata4.00: BMDMA stat 0x26
[   96.454143] ata4.00: failed command: READ DMA EXT
[   96.455341] ata4.00: cmd 25/00:80:b8:96:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   96.457768] ata4.00: status: { DRDY ERR }
[   96.458978] ata4.00: error: { ICRC ABRT }
[   96.460189] ata4: soft resetting link
[   96.632230] ata4.00: configured for MWDMA2
[   96.632240] ata4: EH complete
[   96.650262] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   96.650296] ata4.00: BMDMA stat 0x26
[   96.650315] ata4.00: failed command: READ DMA EXT
[   96.650341] ata4.00: cmd 25/00:80:b8:96:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   96.650413] ata4.00: status: { DRDY ERR }
[   96.650433] ata4.00: error: { ICRC ABRT }
[   96.650458] ata4: soft resetting link
[   96.820229] ata4.00: configured for MWDMA2
[   96.820235] ata4: EH complete
[   96.838842] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   96.838877] ata4.00: BMDMA stat 0x26
[   96.838897] ata4.00: failed command: READ DMA EXT
[   96.838923] ata4.00: cmd 25/00:80:b8:97:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   96.838996] ata4.00: status: { DRDY ERR }
[   96.839015] ata4.00: error: { ICRC ABRT }
[   96.839040] ata4: soft resetting link
[   97.008228] ata4.00: configured for MWDMA2
[   97.008236] ata4: EH complete
[   97.026193] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   97.026224] ata4.00: BMDMA stat 0x26
[   97.026244] ata4.00: failed command: READ DMA EXT
[   97.026270] ata4.00: cmd 25/00:80:b8:97:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   97.026342] ata4.00: status: { DRDY ERR }
[   97.026362] ata4.00: error: { ICRC ABRT }
[   97.026387] ata4: soft resetting link
[   97.196227] ata4.00: configured for MWDMA2
[   97.196234] ata4: EH complete
[   97.214235] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   97.215499] ata4.00: BMDMA stat 0x26
[   97.216753] ata4.00: failed command: READ DMA EXT
[   97.217994] ata4.00: cmd 25/00:80:b8:97:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   97.220476] ata4.00: status: { DRDY ERR }
[   97.221683] ata4.00: error: { ICRC ABRT }
[   97.222874] ata4: soft resetting link
[   97.392238] ata4.00: configured for MWDMA2
[   97.392245] ata4: EH complete
[   97.405393] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   97.406614] ata4.00: BMDMA stat 0x26
[   97.407809] ata4.00: failed command: READ DMA EXT
[   97.409017] ata4.00: cmd 25/00:80:b8:99:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   97.411431] ata4.00: status: { DRDY ERR }
[   97.412648] ata4.00: error: { ICRC ABRT }
[   97.413856] ata4: soft resetting link
[   97.584230] ata4.00: configured for MWDMA2
[   97.584240] ata4: EH complete
[   97.593038] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   97.593072] ata4.00: BMDMA stat 0x26
[   97.593091] ata4.00: failed command: READ DMA EXT
[   97.593117] ata4.00: cmd 25/00:80:b8:99:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   97.593190] ata4.00: status: { DRDY ERR }
[   97.593209] ata4.00: error: { ICRC ABRT }
[   97.593234] ata4: soft resetting link
[   97.764229] ata4.00: configured for MWDMA2
[   97.764235] ata4: EH complete
[   97.780625] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   97.780657] ata4.00: BMDMA stat 0x26
[   97.780676] ata4.00: failed command: READ DMA EXT
[   97.780702] ata4.00: cmd 25/00:80:b8:99:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   97.780774] ata4.00: status: { DRDY ERR }
[   97.780794] ata4.00: error: { ICRC ABRT }
[   97.780819] ata4: soft resetting link
[   97.952227] ata4.00: configured for MWDMA2
[   97.952233] ata4: EH complete
[   97.969628] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   97.969663] ata4.00: BMDMA stat 0x26
[   97.969683] ata4.00: failed command: READ DMA EXT
[   97.969709] ata4.00: cmd 25/00:80:b8:9a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   97.969782] ata4.00: status: { DRDY ERR }
[   97.969801] ata4.00: error: { ICRC ABRT }
[   97.969827] ata4: soft resetting link
[   98.140227] ata4.00: configured for MWDMA2
[   98.140235] ata4: EH complete
[   98.157274] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   98.158554] ata4.00: BMDMA stat 0x26
[   98.159824] ata4.00: failed command: READ DMA EXT
[   98.161095] ata4.00: cmd 25/00:80:b8:9a:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   98.163644] ata4.00: status: { DRDY ERR }
[   98.164934] ata4.00: error: { ICRC ABRT }
[   98.166206] ata4: soft resetting link
[   98.336226] ata4.00: configured for MWDMA2
[   98.336233] ata4: EH complete
[   98.357705] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   98.359006] ata4.00: BMDMA stat 0x26
[   98.360303] ata4.00: failed command: READ DMA EXT
[   98.361576] ata4.00: cmd 25/00:80:b8:9c:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   98.364136] ata4.00: status: { DRDY ERR }
[   98.365374] ata4.00: error: { ICRC ABRT }
[   98.366579] ata4: soft resetting link
[   98.536230] ata4.00: configured for MWDMA2
[   98.536239] ata4: EH complete
[   98.545713] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   98.545746] ata4.00: BMDMA stat 0x26
[   98.545766] ata4.00: failed command: READ DMA EXT
[   98.545792] ata4.00: cmd 25/00:80:38:9d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   98.545864] ata4.00: status: { DRDY ERR }
[   98.545884] ata4.00: error: { ICRC ABRT }
[   98.545909] ata4: soft resetting link
[   98.716232] ata4.00: configured for MWDMA2
[   98.716240] ata4: EH complete
[   98.733356] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   98.733388] ata4.00: BMDMA stat 0x26
[   98.733407] ata4.00: failed command: READ DMA EXT
[   98.733433] ata4.00: cmd 25/00:80:38:9d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   98.733505] ata4.00: status: { DRDY ERR }
[   98.733525] ata4.00: error: { ICRC ABRT }
[   98.733550] ata4: soft resetting link
[   98.904230] ata4.00: configured for MWDMA2
[   98.904237] ata4: EH complete
[   98.921666] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   98.921701] ata4.00: BMDMA stat 0x26
[   98.921721] ata4.00: failed command: READ DMA EXT
[   98.921748] ata4.00: cmd 25/00:80:b8:9d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   98.921820] ata4.00: status: { DRDY ERR }
[   98.921840] ata4.00: error: { ICRC ABRT }
[   98.921865] ata4: soft resetting link
[   99.092228] ata4.00: configured for MWDMA2
[   99.092236] ata4: EH complete
[   99.109293] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   99.110569] ata4.00: BMDMA stat 0x26
[   99.111841] ata4.00: failed command: READ DMA EXT
[   99.113106] ata4.00: cmd 25/00:80:b8:9d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   99.115642] ata4.00: status: { DRDY ERR }
[   99.116924] ata4.00: error: { ICRC ABRT }
[   99.118189] ata4: soft resetting link
[   99.288226] ata4.00: configured for MWDMA2
[   99.288232] ata4: EH complete
[   99.307883] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   99.309175] ata4.00: BMDMA stat 0x26
[   99.310441] ata4.00: failed command: READ DMA EXT
[   99.311702] ata4.00: cmd 25/00:80:b8:9d:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[   99.314219] ata4.00: status: { DRDY ERR }
[   99.315436] ata4.00: error: { ICRC ABRT }
[   99.316649] ata4: soft resetting link
[   99.488228] ata4.00: configured for MWDMA2
[   99.488234] ata4: EH complete
[  129.884199] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  129.884238] ata4.00: failed command: READ DMA EXT
[  129.884265] ata4.00: cmd 25/00:80:38:a4:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  129.884334] ata4.00: status: { DRDY }
[  134.924037] ata4: link is slow to respond, please be patient (ready=0)
[  139.908038] ata4: device not ready (errno=-16), forcing hardreset
[  139.908045] ata4: soft resetting link
[  143.496229] ata4.00: configured for MWDMA2
[  143.496240] ata4: EH complete
[  143.501853] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  143.501886] ata4.00: BMDMA stat 0x26
[  143.501906] ata4.00: failed command: READ DMA EXT
[  143.501933] ata4.00: cmd 25/00:80:38:a4:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  143.502005] ata4.00: status: { DRDY ERR }
[  143.502025] ata4.00: error: { ICRC ABRT }
[  143.502050] ata4: soft resetting link
[  143.672230] ata4.00: configured for MWDMA2
[  143.672237] ata4: EH complete
[  143.690041] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  143.690076] ata4.00: BMDMA stat 0x26
[  143.690096] ata4.00: failed command: READ DMA EXT
[  143.690123] ata4.00: cmd 25/00:80:b8:a4:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  143.690195] ata4.00: status: { DRDY ERR }
[  143.690215] ata4.00: error: { ICRC ABRT }
[  143.690240] ata4: soft resetting link
[  143.860229] ata4.00: configured for MWDMA2
[  143.860237] ata4: EH complete
[  143.878244] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  143.878278] ata4.00: BMDMA stat 0x26
[  143.878297] ata4.00: failed command: READ DMA EXT
[  143.878323] ata4.00: cmd 25/00:80:38:a5:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  143.878396] ata4.00: status: { DRDY ERR }
[  143.878415] ata4.00: error: { ICRC ABRT }
[  143.878440] ata4: soft resetting link
[  144.048225] ata4.00: configured for MWDMA2
[  144.048233] ata4: EH complete
[  144.067177] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  144.068474] ata4.00: BMDMA stat 0x26
[  144.069737] ata4.00: failed command: READ DMA EXT
[  144.070995] ata4.00: cmd 25/00:80:b8:a6:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  144.073540] ata4.00: status: { DRDY ERR }
[  144.074810] ata4.00: error: { ICRC ABRT }
[  144.076078] ata4: soft resetting link
[  144.248229] ata4.00: configured for MWDMA2
[  144.248238] ata4: EH complete
[  144.269035] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  144.270326] ata4.00: BMDMA stat 0x26
[  144.271593] ata4.00: failed command: READ DMA EXT
[  144.272863] ata4.00: cmd 25/00:80:38:a8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  144.275373] ata4.00: status: { DRDY ERR }
[  144.276593] ata4.00: error: { ICRC ABRT }
[  144.277796] ata4: soft resetting link
[  144.448232] ata4.00: configured for MWDMA2
[  144.448240] ata4: EH complete
[  144.467803] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  144.469028] ata4.00: BMDMA stat 0x26
[  144.470235] ata4.00: failed command: READ DMA EXT
[  144.471439] ata4.00: cmd 25/00:80:38:a8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  144.473882] ata4.00: status: { DRDY ERR }
[  144.475094] ata4.00: error: { ICRC ABRT }
[  144.476304] ata4: soft resetting link
[  144.648227] ata4.00: configured for MWDMA2
[  144.648234] ata4: EH complete
[  144.666378] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  144.666411] ata4.00: BMDMA stat 0x26
[  144.666430] ata4.00: failed command: READ DMA EXT
[  144.666456] ata4.00: cmd 25/00:80:38:a8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  144.666529] ata4.00: status: { DRDY ERR }
[  144.666548] ata4.00: error: { ICRC ABRT }
[  144.666573] ata4: soft resetting link
[  144.836227] ata4.00: configured for MWDMA2
[  144.836234] ata4: EH complete
[  144.855067] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  144.855100] ata4.00: BMDMA stat 0x26
[  144.855120] ata4.00: failed command: READ DMA EXT
[  144.855147] ata4.00: cmd 25/00:80:b8:a8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  144.855219] ata4.00: status: { DRDY ERR }
[  144.855239] ata4.00: error: { ICRC ABRT }
[  144.855264] ata4: soft resetting link
[  145.024231] ata4.00: configured for MWDMA2
[  145.024239] ata4: EH complete
[  145.042381] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  145.042413] ata4.00: BMDMA stat 0x26
[  145.042432] ata4.00: failed command: READ DMA EXT
[  145.042459] ata4.00: cmd 25/00:80:b8:a8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  145.042531] ata4.00: status: { DRDY ERR }
[  145.042551] ata4.00: error: { ICRC ABRT }
[  145.042575] ata4: soft resetting link
[  145.212228] ata4.00: configured for MWDMA2
[  145.212234] ata4: EH complete
[  145.230087] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  145.231377] ata4.00: BMDMA stat 0x26
[  145.232645] ata4.00: failed command: READ DMA EXT
[  145.233899] ata4.00: cmd 25/00:80:b8:a8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  145.236402] ata4.00: status: { DRDY ERR }
[  145.237613] ata4.00: error: { ICRC ABRT }
[  145.238809] ata4: soft resetting link
[  145.408225] ata4.00: configured for MWDMA2
[  145.408232] ata4: EH complete
[  145.420670] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  145.421884] ata4.00: BMDMA stat 0x26
[  145.423089] ata4.00: failed command: READ DMA EXT
[  145.424300] ata4.00: cmd 25/00:80:b8:ab:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  145.426723] ata4.00: status: { DRDY ERR }
[  145.427939] ata4.00: error: { ICRC ABRT }
[  145.429158] ata4: soft resetting link
[  145.600232] ata4.00: configured for MWDMA2
[  145.600242] ata4: EH complete
[  145.621289] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  145.621329] ata4.00: BMDMA stat 0x26
[  145.621349] ata4.00: failed command: READ DMA EXT
[  145.621376] ata4.00: cmd 25/00:80:38:ae:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  145.621448] ata4.00: status: { DRDY ERR }
[  145.621468] ata4.00: error: { ICRC ABRT }
[  145.621495] ata4: soft resetting link
[  145.792230] ata4.00: configured for MWDMA2
[  145.792238] ata4: EH complete
[  145.809235] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  145.809269] ata4.00: BMDMA stat 0x26
[  145.809288] ata4.00: failed command: READ DMA EXT
[  145.809314] ata4.00: cmd 25/00:80:b8:ae:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  145.809387] ata4.00: status: { DRDY ERR }
[  145.809406] ata4.00: error: { ICRC ABRT }
[  145.809431] ata4: soft resetting link
[  145.980228] ata4.00: configured for MWDMA2
[  145.980236] ata4: EH complete
[  145.996809] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  145.996841] ata4.00: BMDMA stat 0x26
[  145.996861] ata4.00: failed command: READ DMA EXT
[  145.996887] ata4.00: cmd 25/00:80:b8:ae:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  145.996959] ata4.00: status: { DRDY ERR }
[  145.996979] ata4.00: error: { ICRC ABRT }
[  145.997004] ata4: soft resetting link
[  146.168227] ata4.00: configured for MWDMA2
[  146.168234] ata4: EH complete
[  146.185238] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  146.186531] ata4.00: BMDMA stat 0x26
[  146.187793] ata4.00: failed command: READ DMA EXT
[  146.189068] ata4.00: cmd 25/00:80:38:af:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  146.191606] ata4.00: status: { DRDY ERR }
[  146.192889] ata4.00: error: { ICRC ABRT }
[  146.194152] ata4: soft resetting link
[  146.364229] ata4.00: configured for MWDMA2
[  146.364237] ata4: EH complete
[  146.386362] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  146.387654] ata4.00: BMDMA stat 0x26
[  146.388949] ata4.00: failed command: READ DMA EXT
[  146.390209] ata4.00: cmd 25/00:80:b8:b1:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  146.392721] ata4.00: status: { DRDY ERR }
[  146.393936] ata4.00: error: { ICRC ABRT }
[  146.395141] ata4: soft resetting link
[  146.564229] ata4.00: configured for MWDMA2
[  146.564238] ata4: EH complete
[  146.579013] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  146.579051] ata4.00: BMDMA stat 0x26
[  146.579071] ata4.00: failed command: READ DMA EXT
[  146.579097] ata4.00: cmd 25/00:80:38:b6:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  146.579170] ata4.00: status: { DRDY ERR }
[  146.579190] ata4.00: error: { ICRC ABRT }
[  146.579216] ata4: soft resetting link
[  146.748227] ata4.00: configured for MWDMA2
[  146.748235] ata4: EH complete
[  146.766841] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  146.766872] ata4.00: BMDMA stat 0x26
[  146.766892] ata4.00: failed command: READ DMA EXT
[  146.766918] ata4.00: cmd 25/00:80:38:b6:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  146.766990] ata4.00: status: { DRDY ERR }
[  146.767010] ata4.00: error: { ICRC ABRT }
[  146.767035] ata4: soft resetting link
[  146.936228] ata4.00: configured for MWDMA2
[  146.936236] ata4: EH complete
[  146.954895] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  146.954930] ata4.00: BMDMA stat 0x26
[  146.954949] ata4.00: failed command: READ DMA EXT
[  146.954976] ata4.00: cmd 25/00:80:b8:b6:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  146.955048] ata4.00: status: { DRDY ERR }
[  146.955068] ata4.00: error: { ICRC ABRT }
[  146.955093] ata4: soft resetting link
[  147.124230] ata4.00: configured for MWDMA2
[  147.124238] ata4: EH complete
[  147.143941] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  147.145240] ata4.00: BMDMA stat 0x26
[  147.146502] ata4.00: failed command: READ DMA EXT
[  147.147760] ata4.00: cmd 25/00:80:38:b8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  147.150307] ata4.00: status: { DRDY ERR }
[  147.151580] ata4.00: error: { ICRC ABRT }
[  147.152850] ata4: soft resetting link
[  147.324230] ata4.00: configured for MWDMA2
[  147.324239] ata4: EH complete
[  147.342516] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  147.343800] ata4.00: BMDMA stat 0x26
[  147.345077] ata4.00: failed command: READ DMA EXT
[  147.346337] ata4.00: cmd 25/00:80:38:b8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  147.348851] ata4.00: status: { DRDY ERR }
[  147.350066] ata4.00: error: { ICRC ABRT }
[  147.351270] ata4: soft resetting link
[  147.520222] ata4.00: configured for MWDMA2
[  147.520229] ata4: EH complete
[  147.531976] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  147.532025] ata4.00: BMDMA stat 0x26
[  147.532046] ata4.00: failed command: READ DMA EXT
[  147.532072] ata4.00: cmd 25/00:80:b8:b9:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  147.532145] ata4.00: status: { DRDY ERR }
[  147.532165] ata4.00: error: { ICRC ABRT }
[  147.532190] ata4: soft resetting link
[  147.704229] ata4.00: configured for MWDMA2
[  147.704237] ata4: EH complete
[  147.719264] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  147.719295] ata4.00: BMDMA stat 0x26
[  147.719315] ata4.00: failed command: READ DMA EXT
[  147.719341] ata4.00: cmd 25/00:80:b8:b9:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  147.719413] ata4.00: status: { DRDY ERR }
[  147.719433] ata4.00: error: { ICRC ABRT }
[  147.719457] ata4: soft resetting link
[  147.888229] ata4.00: configured for MWDMA2
[  147.888236] ata4: EH complete
[  147.908672] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  147.908709] ata4.00: BMDMA stat 0x26
[  147.908729] ata4.00: failed command: READ DMA EXT
[  147.908756] ata4.00: cmd 25/00:80:b8:bb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  147.908828] ata4.00: status: { DRDY ERR }
[  147.908848] ata4.00: error: { ICRC ABRT }
[  147.908874] ata4: soft resetting link
[  148.080237] ata4.00: configured for MWDMA2
[  148.080245] ata4: EH complete
[  148.099012] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  148.100292] ata4.00: BMDMA stat 0x26
[  148.101548] ata4.00: failed command: READ DMA EXT
[  148.102798] ata4.00: cmd 25/00:80:b8:be:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  148.105331] ata4.00: status: { DRDY ERR }
[  148.106597] ata4.00: error: { ICRC ABRT }
[  148.107857] ata4: soft resetting link
[  148.276227] ata4.00: configured for MWDMA2
[  148.276236] ata4: EH complete
[  148.287853] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  148.289158] ata4.00: BMDMA stat 0x26
[  148.290421] ata4.00: failed command: READ DMA EXT
[  148.291675] ata4.00: cmd 25/00:80:38:c0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  148.294180] ata4.00: status: { DRDY ERR }
[  148.295390] ata4.00: error: { ICRC ABRT }
[  148.296592] ata4: soft resetting link
[  148.468232] ata4.00: configured for MWDMA2
[  148.468240] ata4: EH complete
[  148.486196] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  148.487412] ata4.00: BMDMA stat 0x26
[  148.488622] ata4.00: failed command: READ DMA EXT
[  148.489823] ata4.00: cmd 25/00:80:38:c0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  148.492252] ata4.00: status: { DRDY ERR }
[  148.493473] ata4.00: error: { ICRC ABRT }
[  148.493480] ata4: soft resetting link
[  148.664230] ata4.00: configured for MWDMA2
[  148.664237] ata4: EH complete
[  148.674103] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  148.674136] ata4.00: BMDMA stat 0x26
[  148.674155] ata4.00: failed command: READ DMA EXT
[  148.674181] ata4.00: cmd 25/00:80:38:c0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  148.674253] ata4.00: status: { DRDY ERR }
[  148.674273] ata4.00: error: { ICRC ABRT }
[  148.674298] ata4: soft resetting link
[  148.844229] ata4.00: configured for MWDMA2
[  148.844235] ata4: EH complete
[  148.862493] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  148.862528] ata4.00: BMDMA stat 0x26
[  148.862547] ata4.00: failed command: READ DMA EXT
[  148.862573] ata4.00: cmd 25/00:80:b8:c0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  148.862646] ata4.00: status: { DRDY ERR }
[  148.862665] ata4.00: error: { ICRC ABRT }
[  148.862690] ata4: soft resetting link
[  149.032229] ata4.00: configured for MWDMA2
[  149.032236] ata4: EH complete
[  149.050917] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  149.050951] ata4.00: BMDMA stat 0x26
[  149.050971] ata4.00: failed command: READ DMA EXT
[  149.050998] ata4.00: cmd 25/00:80:b8:c1:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  149.051070] ata4.00: status: { DRDY ERR }
[  149.051090] ata4.00: error: { ICRC ABRT }
[  149.051115] ata4: soft resetting link
[  149.220228] ata4.00: configured for MWDMA2
[  149.220236] ata4: EH complete
[  149.238701] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  149.239967] ata4.00: BMDMA stat 0x26
[  149.241236] ata4.00: failed command: READ DMA EXT
[  149.242498] ata4.00: cmd 25/00:80:b8:c1:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  149.245026] ata4.00: status: { DRDY ERR }
[  149.246266] ata4.00: error: { ICRC ABRT }
[  149.247471] ata4: soft resetting link
[  149.416230] ata4.00: configured for MWDMA2
[  149.416237] ata4: EH complete
[  149.428174] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  149.429391] ata4.00: BMDMA stat 0x26
[  149.430598] ata4.00: failed command: READ DMA EXT
[  149.431809] ata4.00: cmd 25/00:80:38:c3:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  149.434248] ata4.00: status: { DRDY ERR }
[  149.435469] ata4.00: error: { ICRC ABRT }
[  149.436687] ata4: soft resetting link
[  149.608229] ata4.00: configured for MWDMA2
[  149.608239] ata4: EH complete
[  149.626322] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  149.626355] ata4.00: BMDMA stat 0x26
[  149.626374] ata4.00: failed command: READ DMA EXT
[  149.626400] ata4.00: cmd 25/00:80:38:c3:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  149.626472] ata4.00: status: { DRDY ERR }
[  149.626492] ata4.00: error: { ICRC ABRT }
[  149.626517] ata4: soft resetting link
[  149.796229] ata4.00: configured for MWDMA2
[  149.796235] ata4: EH complete
[  149.814890] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  149.814924] ata4.00: BMDMA stat 0x26
[  149.814944] ata4.00: failed command: READ DMA EXT
[  149.814971] ata4.00: cmd 25/00:80:b8:c3:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  149.815043] ata4.00: status: { DRDY ERR }
[  149.815063] ata4.00: error: { ICRC ABRT }
[  149.815088] ata4: soft resetting link
[  149.984234] ata4.00: configured for MWDMA2
[  149.984241] ata4: EH complete
[  150.005903] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  150.005941] ata4.00: BMDMA stat 0x26
[  150.005961] ata4.00: failed command: READ DMA EXT
[  150.005987] ata4.00: cmd 25/00:80:b8:c5:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  150.006061] ata4.00: status: { DRDY ERR }
[  150.006080] ata4.00: error: { ICRC ABRT }
[  150.006106] ata4: soft resetting link
[  150.176230] ata4.00: configured for MWDMA2
[  150.176238] ata4: EH complete
[  150.193469] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  150.194738] ata4.00: BMDMA stat 0x26
[  150.196010] ata4.00: failed command: READ DMA EXT
[  150.197272] ata4.00: cmd 25/00:80:b8:c5:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  150.199815] ata4.00: status: { DRDY ERR }
[  150.201098] ata4.00: error: { ICRC ABRT }
[  150.202370] ata4: soft resetting link
[  150.372228] ata4.00: configured for MWDMA2
[  150.372235] ata4: EH complete
[  150.382660] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  150.383948] ata4.00: BMDMA stat 0x26
[  150.385240] ata4.00: failed command: READ DMA EXT
[  150.386511] ata4.00: cmd 25/00:80:38:c7:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  150.389032] ata4.00: status: { DRDY ERR }
[  150.390256] ata4.00: error: { ICRC ABRT }
[  150.391470] ata4: soft resetting link
[  150.560230] ata4.00: configured for MWDMA2
[  150.560239] ata4: EH complete
[  150.572017] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  150.572054] ata4.00: BMDMA stat 0x26
[  150.572074] ata4.00: failed command: READ DMA EXT
[  150.572101] ata4.00: cmd 25/00:80:38:c9:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  150.572173] ata4.00: status: { DRDY ERR }
[  150.572193] ata4.00: error: { ICRC ABRT }
[  150.572219] ata4: soft resetting link
[  150.744231] ata4.00: configured for MWDMA2
[  150.744239] ata4: EH complete
[  150.760365] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  150.760400] ata4.00: BMDMA stat 0x26
[  150.760419] ata4.00: failed command: READ DMA EXT
[  150.760446] ata4.00: cmd 25/00:80:38:ca:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  150.760518] ata4.00: status: { DRDY ERR }
[  150.760538] ata4.00: error: { ICRC ABRT }
[  150.760563] ata4: soft resetting link
[  150.932229] ata4.00: configured for MWDMA2
[  150.932237] ata4: EH complete
[  150.948041] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  150.948073] ata4.00: BMDMA stat 0x26
[  150.948093] ata4.00: failed command: READ DMA EXT
[  150.948119] ata4.00: cmd 25/00:80:38:ca:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  150.948192] ata4.00: status: { DRDY ERR }
[  150.948212] ata4.00: error: { ICRC ABRT }
[  150.948237] ata4: soft resetting link
[  151.120224] ata4.00: configured for MWDMA2
[  151.120231] ata4: EH complete
[  151.136742] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  151.137998] ata4.00: BMDMA stat 0x26
[  151.139230] ata4.00: failed command: READ DMA EXT
[  151.140481] ata4.00: cmd 25/00:80:38:cb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  151.142979] ata4.00: status: { DRDY ERR }
[  151.144226] ata4.00: error: { ICRC ABRT }
[  151.145476] ata4: soft resetting link
[  151.316235] ata4.00: configured for MWDMA2
[  151.316243] ata4: EH complete
[  151.335180] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  151.336458] ata4.00: BMDMA stat 0x26
[  151.337702] ata4.00: failed command: READ DMA EXT
[  151.338947] ata4.00: cmd 25/00:80:38:cb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  151.341459] ata4.00: status: { DRDY ERR }
[  151.342665] ata4.00: error: { ICRC ABRT }
[  151.343874] ata4: soft resetting link
[  151.512228] ata4.00: configured for MWDMA2
[  151.512235] ata4: EH complete
[  151.524251] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  151.524288] ata4.00: BMDMA stat 0x26
[  151.524308] ata4.00: failed command: READ DMA EXT
[  151.524334] ata4.00: cmd 25/00:80:38:cc:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  151.524407] ata4.00: status: { DRDY ERR }
[  151.524427] ata4.00: error: { ICRC ABRT }
[  151.524452] ata4: soft resetting link
[  151.696231] ata4.00: configured for MWDMA2
[  151.696238] ata4: EH complete
[  151.713119] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  151.713155] ata4.00: BMDMA stat 0x26
[  151.713174] ata4.00: failed command: READ DMA EXT
[  151.713201] ata4.00: cmd 25/00:80:b8:cd:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  151.713274] ata4.00: status: { DRDY ERR }
[  151.713294] ata4.00: error: { ICRC ABRT }
[  151.713319] ata4: soft resetting link
[  151.884235] ata4.00: configured for MWDMA2
[  151.884243] ata4: EH complete
[  151.900248] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  151.900280] ata4.00: BMDMA stat 0x26
[  151.900299] ata4.00: failed command: READ DMA EXT
[  151.900326] ata4.00: cmd 25/00:80:b8:cd:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  151.900398] ata4.00: status: { DRDY ERR }
[  151.900418] ata4.00: error: { ICRC ABRT }
[  151.900443] ata4: soft resetting link
[  152.072229] ata4.00: configured for MWDMA2
[  152.072236] ata4: EH complete
[  152.088740] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  152.089988] ata4.00: BMDMA stat 0x26
[  152.091236] ata4.00: failed command: READ DMA EXT
[  152.092493] ata4.00: cmd 25/00:80:38:ce:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  152.095030] ata4.00: status: { DRDY ERR }
[  152.096296] ata4.00: error: { ICRC ABRT }
[  152.097548] ata4: soft resetting link
[  152.268231] ata4.00: configured for MWDMA2
[  152.268238] ata4: EH complete
[  152.288075] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  152.289355] ata4.00: BMDMA stat 0x26
[  152.290610] ata4.00: failed command: READ DMA EXT
[  152.291857] ata4.00: cmd 25/00:80:b8:ce:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  152.294365] ata4.00: status: { DRDY ERR }
[  152.295570] ata4.00: error: { ICRC ABRT }
[  152.296769] ata4: soft resetting link
[  152.468226] ata4.00: configured for MWDMA2
[  152.468234] ata4: EH complete
[  152.487899] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  152.489131] ata4.00: BMDMA stat 0x26
[  152.490331] ata4.00: failed command: READ DMA EXT
[  152.491524] ata4.00: cmd 25/00:80:38:d0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  152.493948] ata4.00: status: { DRDY ERR }
[  152.495167] ata4.00: error: { ICRC ABRT }
[  152.495175] ata4: soft resetting link
[  152.664227] ata4.00: configured for MWDMA2
[  152.664236] ata4: EH complete
[  152.676273] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  152.676310] ata4.00: BMDMA stat 0x26
[  152.676329] ata4.00: failed command: READ DMA EXT
[  152.676356] ata4.00: cmd 25/00:80:b8:d0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  152.676428] ata4.00: status: { DRDY ERR }
[  152.676447] ata4.00: error: { ICRC ABRT }
[  152.676472] ata4: soft resetting link
[  152.848229] ata4.00: configured for MWDMA2
[  152.848237] ata4: EH complete
[  152.863549] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  152.863581] ata4.00: BMDMA stat 0x26
[  152.863600] ata4.00: failed command: READ DMA EXT
[  152.863626] ata4.00: cmd 25/00:80:b8:d0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  152.863699] ata4.00: status: { DRDY ERR }
[  152.863719] ata4.00: error: { ICRC ABRT }
[  152.863744] ata4: soft resetting link
[  153.042697] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  153.042699] ata4.00: revalidation failed (errno=-5)
[  158.016241] ata4: soft resetting link
[  158.188229] ata4.00: configured for MWDMA2
[  158.188237] ata4: EH complete
[  158.199407] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  158.199444] ata4.00: BMDMA stat 0x26
[  158.199463] ata4.00: failed command: READ DMA EXT
[  158.199490] ata4.00: cmd 25/00:80:b8:d1:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  158.199563] ata4.00: status: { DRDY ERR }
[  158.199583] ata4.00: error: { ICRC ABRT }
[  158.199608] ata4: soft resetting link
[  158.368230] ata4.00: configured for MWDMA2
[  158.368239] ata4: EH complete
[  158.389417] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  158.389453] ata4.00: BMDMA stat 0x26
[  158.389473] ata4.00: failed command: READ DMA EXT
[  158.389499] ata4.00: cmd 25/00:80:b8:d2:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  158.389572] ata4.00: status: { DRDY ERR }
[  158.389592] ata4.00: error: { ICRC ABRT }
[  158.389617] ata4: soft resetting link
[  158.560232] ata4.00: configured for MWDMA2
[  158.560241] ata4: EH complete
[  158.577529] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  158.577564] ata4.00: BMDMA stat 0x26
[  158.577584] ata4.00: failed command: READ DMA EXT
[  158.577611] ata4.00: cmd 25/00:80:38:d3:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  158.577683] ata4.00: status: { DRDY ERR }
[  158.577703] ata4.00: error: { ICRC ABRT }
[  158.577728] ata4: soft resetting link
[  158.748230] ata4.00: configured for MWDMA2
[  158.748237] ata4: EH complete
[  158.766131] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  158.766167] ata4.00: BMDMA stat 0x26
[  158.766186] ata4.00: failed command: READ DMA EXT
[  158.766213] ata4.00: cmd 25/00:80:38:d4:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  158.766285] ata4.00: status: { DRDY ERR }
[  158.766305] ata4.00: error: { ICRC ABRT }
[  158.766331] ata4: soft resetting link
[  158.936234] ata4.00: configured for MWDMA2
[  158.936241] ata4: EH complete
[  158.953712] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  158.953744] ata4.00: BMDMA stat 0x26
[  158.953763] ata4.00: failed command: READ DMA EXT
[  158.953789] ata4.00: cmd 25/00:80:38:d4:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  158.953862] ata4.00: status: { DRDY ERR }
[  158.953881] ata4.00: error: { ICRC ABRT }
[  158.953906] ata4: soft resetting link
[  159.124230] ata4.00: configured for MWDMA2
[  159.124236] ata4: EH complete
[  159.142222] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  159.143565] ata4.00: BMDMA stat 0x26
[  159.144934] ata4.00: failed command: READ DMA EXT
[  159.146293] ata4.00: cmd 25/00:80:b8:d4:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  159.149014] ata4.00: status: { DRDY ERR }
[  159.150352] ata4.00: error: { ICRC ABRT }
[  159.151656] ata4: soft resetting link
[  159.320226] ata4.00: configured for MWDMA2
[  159.320233] ata4: EH complete
[  159.334601] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  159.335918] ata4.00: BMDMA stat 0x26
[  159.337236] ata4.00: failed command: READ DMA EXT
[  159.338538] ata4.00: cmd 25/00:80:b8:da:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  159.341179] ata4.00: status: { DRDY ERR }
[  159.342509] ata4.00: error: { ICRC ABRT }
[  159.343821] ata4: soft resetting link
[  159.512232] ata4.00: configured for MWDMA2
[  159.512241] ata4: EH complete
[  159.523034] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  159.523070] ata4.00: BMDMA stat 0x26
[  159.523090] ata4.00: failed command: READ DMA EXT
[  159.523117] ata4.00: cmd 25/00:80:b8:db:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  159.523189] ata4.00: status: { DRDY ERR }
[  159.523209] ata4.00: error: { ICRC ABRT }
[  159.523234] ata4: soft resetting link
[  159.692230] ata4.00: configured for MWDMA2
[  159.692238] ata4: EH complete
[  159.711679] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  159.711714] ata4.00: BMDMA stat 0x26
[  159.711734] ata4.00: failed command: READ DMA EXT
[  159.711760] ata4.00: cmd 25/00:80:b8:dc:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  159.711833] ata4.00: status: { DRDY ERR }
[  159.711853] ata4.00: error: { ICRC ABRT }
[  159.711878] ata4: soft resetting link
[  159.880229] ata4.00: configured for MWDMA2
[  159.880238] ata4: EH complete
[  159.899217] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  159.899249] ata4.00: BMDMA stat 0x26
[  159.899268] ata4.00: failed command: READ DMA EXT
[  159.899295] ata4.00: cmd 25/00:80:b8:dc:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  159.899367] ata4.00: status: { DRDY ERR }
[  159.899387] ata4.00: error: { ICRC ABRT }
[  159.899412] ata4: soft resetting link
[  160.068228] ata4.00: configured for MWDMA2
[  160.068234] ata4: EH complete
[  160.087450] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  160.088794] ata4.00: BMDMA stat 0x26
[  160.090153] ata4.00: failed command: READ DMA EXT
[  160.091502] ata4.00: cmd 25/00:80:38:dd:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  160.094230] ata4.00: status: { DRDY ERR }
[  160.095591] ata4.00: error: { ICRC ABRT }
[  160.096950] ata4: soft resetting link
[  160.268230] ata4.00: configured for MWDMA2
[  160.268238] ata4: EH complete
[  160.286737] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  160.288125] ata4.00: BMDMA stat 0x26
[  160.289488] ata4.00: failed command: READ DMA EXT
[  160.290838] ata4.00: cmd 25/00:80:b8:dd:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  160.293523] ata4.00: status: { DRDY ERR }
[  160.294818] ata4.00: error: { ICRC ABRT }
[  160.296103] ata4: soft resetting link
[  160.468230] ata4.00: configured for MWDMA2
[  160.468238] ata4: EH complete
[  160.485081] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  160.486353] ata4.00: BMDMA stat 0x26
[  160.487615] ata4.00: failed command: READ DMA EXT
[  160.488886] ata4.00: cmd 25/00:80:b8:dd:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  160.491409] ata4.00: status: { DRDY ERR }
[  160.492675] ata4.00: error: { ICRC ABRT }
[  160.493924] ata4: soft resetting link
[  160.664226] ata4.00: configured for MWDMA2
[  160.664234] ata4: EH complete
[  160.685370] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  160.685405] ata4.00: BMDMA stat 0x26
[  160.685425] ata4.00: failed command: READ DMA EXT
[  160.685451] ata4.00: cmd 25/00:80:38:df:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  160.685524] ata4.00: status: { DRDY ERR }
[  160.685544] ata4.00: error: { ICRC ABRT }
[  160.685569] ata4: soft resetting link
[  160.856231] ata4.00: configured for MWDMA2
[  160.856240] ata4: EH complete
[  160.873946] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  160.873981] ata4.00: BMDMA stat 0x26
[  160.874001] ata4.00: failed command: READ DMA EXT
[  160.874027] ata4.00: cmd 25/00:80:b8:df:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  160.874099] ata4.00: status: { DRDY ERR }
[  160.874119] ata4.00: error: { ICRC ABRT }
[  160.874145] ata4: soft resetting link
[  161.044232] ata4.00: configured for MWDMA2
[  161.044240] ata4: EH complete
[  161.063738] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  161.063773] ata4.00: BMDMA stat 0x26
[  161.063793] ata4.00: failed command: READ DMA EXT
[  161.063820] ata4.00: cmd 25/00:80:b8:e0:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  161.063892] ata4.00: status: { DRDY ERR }
[  161.063912] ata4.00: error: { ICRC ABRT }
[  161.063938] ata4: soft resetting link
[  161.232229] ata4.00: configured for MWDMA2
[  161.232238] ata4: EH complete
[  161.251977] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  161.253295] ata4.00: BMDMA stat 0x26
[  161.254591] ata4.00: failed command: READ DMA EXT
[  161.255887] ata4.00: cmd 25/00:80:38:e1:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  161.258452] ata4.00: status: { DRDY ERR }
[  161.259690] ata4.00: error: { ICRC ABRT }
[  161.260922] ata4: soft resetting link
[  161.432227] ata4.00: configured for MWDMA2
[  161.432235] ata4: EH complete
[  161.453088] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  161.454330] ata4.00: BMDMA stat 0x26
[  161.455552] ata4.00: failed command: READ DMA EXT
[  161.456783] ata4.00: cmd 25/00:80:b8:e3:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  161.459275] ata4.00: status: { DRDY ERR }
[  161.460515] ata4.00: error: { ICRC ABRT }
[  161.461720] ata4: soft resetting link
[  161.632229] ata4.00: configured for MWDMA2
[  161.632238] ata4: EH complete
[  161.655352] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  161.655392] ata4.00: BMDMA stat 0x26
[  161.655412] ata4.00: failed command: READ DMA EXT
[  161.655439] ata4.00: cmd 25/00:80:38:e8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  161.655512] ata4.00: status: { DRDY ERR }
[  161.655532] ata4.00: error: { ICRC ABRT }
[  161.655558] ata4: soft resetting link
[  161.824236] ata4.00: configured for MWDMA2
[  161.824244] ata4: EH complete
[  161.842618] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  161.842650] ata4.00: BMDMA stat 0x26
[  161.842669] ata4.00: failed command: READ DMA EXT
[  161.842695] ata4.00: cmd 25/00:80:38:e8:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  161.842767] ata4.00: status: { DRDY ERR }
[  161.842787] ata4.00: error: { ICRC ABRT }
[  161.842812] ata4: soft resetting link
[  162.012229] ata4.00: configured for MWDMA2
[  162.012235] ata4: EH complete
[  162.031838] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  162.031875] ata4.00: BMDMA stat 0x26
[  162.031894] ata4.00: failed command: READ DMA EXT
[  162.031921] ata4.00: cmd 25/00:80:b8:e9:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  162.031994] ata4.00: status: { DRDY ERR }
[  162.032022] ata4.00: error: { ICRC ABRT }
[  162.032048] ata4: soft resetting link
[  162.204224] ata4.00: configured for MWDMA2
[  162.204232] ata4: EH complete
[  162.220635] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  162.221923] ata4.00: BMDMA stat 0x26
[  162.223192] ata4.00: failed command: READ DMA EXT
[  162.224468] ata4.00: cmd 25/00:80:38:eb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  162.227025] ata4.00: status: { DRDY ERR }
[  162.228309] ata4.00: error: { ICRC ABRT }
[  162.229585] ata4: soft resetting link
[  162.400227] ata4.00: configured for MWDMA2
[  162.400234] ata4: EH complete
[  162.418985] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  162.420286] ata4.00: BMDMA stat 0x26
[  162.421568] ata4.00: failed command: READ DMA EXT
[  162.422846] ata4.00: cmd 25/00:80:38:eb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  162.425404] ata4.00: status: { DRDY ERR }
[  162.426651] ata4.00: error: { ICRC ABRT }
[  162.427857] ata4: soft resetting link
[  162.596225] ata4.00: configured for MWDMA2
[  162.596232] ata4: EH complete
[  162.606935] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  162.606967] ata4.00: BMDMA stat 0x26
[  162.606987] ata4.00: failed command: READ DMA EXT
[  162.607013] ata4.00: cmd 25/00:80:38:eb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  162.607085] ata4.00: status: { DRDY ERR }
[  162.607105] ata4.00: error: { ICRC ABRT }
[  162.607130] ata4: soft resetting link
[  162.776224] ata4.00: configured for MWDMA2
[  162.776231] ata4: EH complete
[  162.794259] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  162.794291] ata4.00: BMDMA stat 0x26
[  162.794310] ata4.00: failed command: READ DMA EXT
[  162.794336] ata4.00: cmd 25/00:80:38:eb:1d/00:00:1d:00:00/e0 tag 0 dma 65536 in
[  162.794408] ata4.00: status: { DRDY ERR }
[  162.794428] ata4.00: error: { ICRC ABRT }
[  162.794453] ata4: soft resetting link
[  162.964231] ata4.00: configured for MWDMA2
[  162.964237] ata4: EH complete
[  168.104474] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  168.104518] ata4.00: BMDMA stat 0x26
[  168.104541] ata4.00: failed command: READ DMA EXT
[  168.104568] ata4.00: cmd 25/00:08:00:ed:51/00:00:1d:00:00/e0 tag 0 dma 4096 in
[  168.104645] ata4.00: status: { DRDY ERR }
[  168.104665] ata4.00: error: { ICRC ABRT }
[  168.104696] ata4: soft resetting link
[  168.276291] ata4.00: configured for MWDMA2
[  168.276314] ata4: EH complete
[  168.582547] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  168.582588] ata4.00: BMDMA stat 0x26
[  168.582608] ata4.00: failed command: READ DMA
[  168.582634] ata4.00: cmd c8/00:08:00:0c:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  168.582707] ata4.00: status: { DRDY ERR }
[  168.582727] ata4.00: error: { ICRC ABRT }
[  168.582755] ata4: soft resetting link
[  168.752267] ata4.00: configured for MWDMA2
[  168.752284] ata4: EH complete
[  168.840689] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  168.840732] ata4.00: BMDMA stat 0x26
[  168.840756] ata4.00: failed command: READ DMA
[  168.840782] ata4.00: cmd c8/00:08:30:c4:25/00:00:00:00:00/e0 tag 0 dma 4096 in
[  168.840862] ata4.00: status: { DRDY ERR }
[  168.840883] ata4.00: error: { ICRC ABRT }
[  168.840911] ata4: soft resetting link
[  169.012247] ata4.00: configured for MWDMA2
[  169.012263] ata4: EH complete
[  169.424977] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  169.425020] ata4.00: BMDMA stat 0x26
[  169.425042] ata4.00: failed command: READ DMA
[  169.425067] ata4.00: cmd c8/00:08:80:28:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  169.425152] ata4.00: status: { DRDY ERR }
[  169.425173] ata4.00: error: { ICRC ABRT }
[  169.425202] ata4: soft resetting link
[  169.596296] ata4.00: configured for MWDMA2
[  169.596316] ata4: EH complete
[  169.630569] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  169.630610] ata4.00: BMDMA stat 0x26
[  169.630631] ata4.00: failed command: READ DMA
[  169.630657] ata4.00: cmd c8/00:00:e0:76:00/00:00:00:00:00/e0 tag 0 dma 131072 in
[  169.630731] ata4.00: status: { DRDY ERR }
[  169.630751] ata4.00: error: { ICRC ABRT }
[  169.630778] ata4: soft resetting link
[  169.800267] ata4.00: configured for MWDMA2
[  169.800283] ata4: EH complete
[  169.807304] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  169.807345] ata4.00: BMDMA stat 0x26
[  169.807366] ata4.00: failed command: READ DMA
[  169.807391] ata4.00: cmd c8/00:00:e0:76:00/00:00:00:00:00/e0 tag 0 dma 131072 in
[  169.807465] ata4.00: status: { DRDY ERR }
[  169.807486] ata4.00: error: { ICRC ABRT }
[  169.807513] ata4: soft resetting link
[  169.976234] ata4.00: configured for MWDMA2
[  169.976248] ata4: EH complete
[  169.983694] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  169.983734] ata4.00: BMDMA stat 0x26
[  169.983755] ata4.00: failed command: READ DMA
[  169.983781] ata4.00: cmd c8/00:00:e0:76:00/00:00:00:00:00/e0 tag 0 dma 131072 in
[  169.983855] ata4.00: status: { DRDY ERR }
[  169.983875] ata4.00: error: { ICRC ABRT }
[  169.983902] ata4: soft resetting link
[  170.152262] ata4.00: configured for MWDMA2
[  170.152281] ata4: EH complete
[  170.160552] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  170.161848] ata4.00: BMDMA stat 0x26
[  170.163114] ata4.00: failed command: READ DMA
[  170.164386] ata4.00: cmd c8/00:00:e0:76:00/00:00:00:00:00/e0 tag 0 dma 131072 in
[  170.166940] ata4.00: status: { DRDY ERR }
[  170.168219] ata4.00: error: { ICRC ABRT }
[  170.169531] ata4: soft resetting link
[  170.340261] ata4.00: configured for MWDMA2
[  170.340277] ata4: EH complete
[  170.348159] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  170.349463] ata4.00: BMDMA stat 0x26
[  170.350745] ata4.00: failed command: READ DMA
[  170.352018] ata4.00: cmd c8/00:00:e0:76:00/00:00:00:00:00/e0 tag 0 dma 131072 in
[  170.354560] ata4.00: status: { DRDY ERR }
[  170.355817] ata4.00: error: { ICRC ABRT }
[  170.357068] ata4: soft resetting link
[  170.528231] ata4.00: configured for MWDMA2
[  170.528246] ata4: EH complete
[  170.535294] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  170.535334] ata4.00: BMDMA stat 0x26
[  170.535355] ata4.00: failed command: READ DMA
[  170.535380] ata4.00: cmd c8/00:00:e0:76:00/00:00:00:00:00/e0 tag 0 dma 131072 in
[  170.535454] ata4.00: status: { DRDY ERR }
[  170.535475] ata4.00: error: { ICRC ABRT }
[  170.535501] ata4: soft resetting link
[  170.704265] ata4.00: configured for MWDMA2
[  170.704688] ata4: EH complete
[  170.725040] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  170.725080] ata4.00: BMDMA stat 0x26
[  170.725101] ata4.00: failed command: READ DMA EXT
[  170.725128] ata4.00: cmd 25/00:08:00:47:0e/00:00:36:00:00/e0 tag 0 dma 4096 in
[  170.727618] ata4.00: status: { DRDY ERR }
[  170.728827] ata4.00: error: { ICRC ABRT }
[  170.729987] ata4: soft resetting link
[  170.900256] ata4.00: configured for MWDMA2
[  170.900273] ata4: EH complete
[  171.191380] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  171.192590] ata4.00: BMDMA stat 0x26
[  171.193755] ata4.00: failed command: READ DMA
[  171.194910] ata4.00: cmd c8/00:08:58:1f:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  171.197290] ata4.00: status: { DRDY ERR }
[  171.198467] ata4.00: error: { ICRC ABRT }
[  171.199696] ata4: soft resetting link
[  171.368283] ata4.00: configured for MWDMA2
[  171.368301] ata4: EH complete
[  171.443609] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  171.444797] ata4.00: BMDMA stat 0x26
[  171.445903] ata4.00: failed command: READ DMA
[  171.446996] ata4.00: cmd c8/00:20:08:6f:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[  171.449230] ata4.00: status: { DRDY ERR }
[  171.450336] ata4.00: error: { ICRC ABRT }
[  171.451477] ata4: soft resetting link
[  171.620248] ata4.00: configured for MWDMA2
[  171.620264] ata4: EH complete
[  171.757974] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  171.758018] ata4.00: BMDMA stat 0x26
[  171.758038] ata4.00: failed command: READ DMA EXT
[  171.758066] ata4.00: cmd 25/00:08:c0:14:6c/00:00:9f:00:00/e0 tag 0 dma 4096 in
[  171.758139] ata4.00: status: { DRDY ERR }
[  171.758159] ata4.00: error: { ICRC ABRT }
[  171.758186] ata4: soft resetting link
[  171.928284] ata4.00: configured for MWDMA2
[  171.928302] ata4: EH complete
[  171.984609] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  171.984650] ata4.00: BMDMA stat 0x26
[  171.984671] ata4.00: failed command: READ DMA EXT
[  171.984698] ata4.00: cmd 25/00:08:80:4e:f3/00:00:9a:00:00/e0 tag 0 dma 4096 in
[  171.984771] ata4.00: status: { DRDY ERR }
[  171.984791] ata4.00: error: { ICRC ABRT }
[  171.984819] ata4: soft resetting link
[  172.156280] ata4.00: configured for MWDMA2
[  172.156298] ata4: EH complete
[  172.364560] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  172.364601] ata4.00: BMDMA stat 0x26
[  172.364626] ata4.00: failed command: READ DMA
[  172.364652] ata4.00: cmd c8/00:08:a8:1d:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  172.364737] ata4.00: status: { DRDY ERR }
[  172.364758] ata4.00: error: { ICRC ABRT }
[  172.364787] ata4: soft resetting link
[  172.536241] ata4.00: configured for MWDMA2
[  172.536255] ata4: EH complete
[  173.118381] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  173.118421] ata4.00: BMDMA stat 0x26
[  173.118441] ata4.00: failed command: READ DMA
[  173.118467] ata4.00: cmd c8/00:08:10:31:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  173.118540] ata4.00: status: { DRDY ERR }
[  173.118560] ata4.00: error: { ICRC ABRT }
[  173.118587] ata4: soft resetting link
[  173.288232] ata4.00: configured for MWDMA2
[  173.288245] ata4: EH complete
[  173.390106] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  173.390146] ata4.00: BMDMA stat 0x26
[  173.390167] ata4.00: failed command: READ DMA
[  173.390192] ata4.00: cmd c8/00:08:90:2a:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  173.390265] ata4.00: status: { DRDY ERR }
[  173.390285] ata4.00: error: { ICRC ABRT }
[  173.390313] ata4: soft resetting link
[  173.560229] ata4.00: configured for MWDMA2
[  173.560243] ata4: EH complete
[  174.012180] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  174.012220] ata4.00: BMDMA stat 0x26
[  174.012241] ata4.00: failed command: READ DMA
[  174.012266] ata4.00: cmd c8/00:08:d8:15:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  174.012340] ata4.00: status: { DRDY ERR }
[  174.012360] ata4.00: error: { ICRC ABRT }
[  174.012387] ata4: soft resetting link
[  174.184239] ata4.00: configured for MWDMA2
[  174.184252] ata4: EH complete
[  174.289072] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  174.289112] ata4.00: BMDMA stat 0x26
[  174.289133] ata4.00: failed command: READ DMA
[  174.289158] ata4.00: cmd c8/00:08:20:54:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  174.289231] ata4.00: status: { DRDY ERR }
[  174.289251] ata4.00: error: { ICRC ABRT }
[  174.289278] ata4: soft resetting link
[  174.460240] ata4.00: configured for MWDMA2
[  174.460254] ata4: EH complete
[  174.600705] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  174.600745] ata4.00: BMDMA stat 0x26
[  174.600765] ata4.00: failed command: READ DMA
[  174.600791] ata4.00: cmd c8/00:08:b0:33:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  174.600864] ata4.00: status: { DRDY ERR }
[  174.600884] ata4.00: error: { ICRC ABRT }
[  174.600911] ata4: soft resetting link
[  174.772227] ata4.00: configured for MWDMA2
[  174.772241] ata4: EH complete
[  175.012874] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  175.012913] ata4.00: BMDMA stat 0x26
[  175.012933] ata4.00: failed command: READ DMA
[  175.012959] ata4.00: cmd c8/00:08:e0:10:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  175.013032] ata4.00: status: { DRDY ERR }
[  175.013052] ata4.00: error: { ICRC ABRT }
[  175.013079] ata4: soft resetting link
[  175.184239] ata4.00: configured for MWDMA2
[  175.184254] ata4: EH complete
[  175.189466] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  175.189504] ata4.00: BMDMA stat 0x26
[  175.189524] ata4.00: failed command: READ DMA
[  175.189550] ata4.00: cmd c8/00:08:e0:10:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  175.189623] ata4.00: status: { DRDY ERR }
[  175.189643] ata4.00: error: { ICRC ABRT }
[  175.189669] ata4: soft resetting link
[  175.364253] ata4.00: configured for MWDMA2
[  175.364271] ata4: EH complete
[  175.423989] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  175.425141] ata4.00: BMDMA stat 0x26
[  175.426300] ata4.00: failed command: READ DMA
[  175.427433] ata4.00: cmd c8/00:08:e8:c7:25/00:00:00:00:00/e0 tag 0 dma 4096 in
[  175.429746] ata4.00: status: { DRDY ERR }
[  175.430920] ata4.00: error: { ICRC ABRT }
[  175.432048] ata4: soft resetting link
[  175.604225] ata4.00: configured for MWDMA2
[  175.604239] ata4: EH complete
[  175.702914] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  175.702954] ata4.00: BMDMA stat 0x26
[  175.702975] ata4.00: failed command: READ DMA
[  175.703001] ata4.00: cmd c8/00:08:30:b3:25/00:00:00:00:00/e0 tag 0 dma 4096 in
[  175.703074] ata4.00: status: { DRDY ERR }
[  175.703094] ata4.00: error: { ICRC ABRT }
[  175.703121] ata4: soft resetting link
[  175.872231] ata4.00: configured for MWDMA2
[  175.872243] ata4: EH complete
[  176.195238] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  176.195277] ata4.00: BMDMA stat 0x26
[  176.195298] ata4.00: failed command: READ DMA
[  176.195323] ata4.00: cmd c8/00:08:18:13:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  176.195396] ata4.00: status: { DRDY ERR }
[  176.195416] ata4.00: error: { ICRC ABRT }
[  176.195443] ata4: soft resetting link
[  176.364228] ata4.00: configured for MWDMA2
[  176.364240] ata4: EH complete
[  176.498441] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  176.498480] ata4.00: BMDMA stat 0x26
[  176.498501] ata4.00: failed command: READ DMA
[  176.498526] ata4.00: cmd c8/00:08:b0:25:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  176.498599] ata4.00: status: { DRDY ERR }
[  176.498619] ata4.00: error: { ICRC ABRT }
[  176.498646] ata4: soft resetting link
[  176.668276] ata4.00: configured for MWDMA2
[  176.668295] ata4: EH complete
[  176.860589] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  176.860636] ata4.00: BMDMA stat 0x26
[  176.860661] ata4.00: failed command: READ DMA
[  176.860687] ata4.00: cmd c8/00:08:c0:55:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  176.860769] ata4.00: status: { DRDY ERR }
[  176.860790] ata4.00: error: { ICRC ABRT }
[  176.860819] ata4: soft resetting link
[  177.088279] ata4.00: configured for MWDMA2
[  177.088303] ata4: EH complete
[  177.224600] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  177.224644] ata4.00: BMDMA stat 0x26
[  177.224665] ata4.00: failed command: READ DMA EXT
[  177.224693] ata4.00: cmd 25/00:08:40:f9:bc/00:00:e4:00:00/e0 tag 0 dma 4096 in
[  177.224767] ata4.00: status: { DRDY ERR }
[  177.224787] ata4.00: error: { ICRC ABRT }
[  177.224817] ata4: soft resetting link
[  177.396278] ata4.00: configured for MWDMA2
[  177.396302] ata4: EH complete
[  178.012406] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  178.012450] ata4.00: BMDMA stat 0x26
[  178.012472] ata4.00: failed command: READ DMA EXT
[  178.012500] ata4.00: cmd 25/00:08:28:8b:2c/00:00:71:00:00/e0 tag 0 dma 4096 in
[  178.012576] ata4.00: status: { DRDY ERR }
[  178.012596] ata4.00: error: { ICRC ABRT }
[  178.012624] ata4: soft resetting link
[  178.184292] ata4.00: configured for MWDMA2
[  178.184313] ata4: EH complete
[  178.328046] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  178.328086] ata4.00: BMDMA stat 0x26
[  178.328107] ata4.00: failed command: READ DMA
[  178.328132] ata4.00: cmd c8/00:08:08:78:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  178.328206] ata4.00: status: { DRDY ERR }
[  178.328226] ata4.00: error: { ICRC ABRT }
[  178.328252] ata4: soft resetting link
[  178.500229] ata4.00: configured for MWDMA2
[  178.500243] ata4: EH complete
[  178.889840] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  178.889882] ata4.00: BMDMA stat 0x26
[  178.889904] ata4.00: failed command: READ DMA EXT
[  178.889931] ata4.00: cmd 25/00:00:e0:07:be/00:01:19:00:00/e0 tag 0 dma 131072 in
[  178.890007] ata4.00: status: { DRDY ERR }
[  178.890028] ata4.00: error: { ICRC ABRT }
[  178.890057] ata4: soft resetting link
[  179.060241] ata4.00: configured for MWDMA2
[  179.060256] ata4: EH complete
[  179.092361] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  179.092402] ata4.00: BMDMA stat 0x26
[  179.092423] ata4.00: failed command: READ DMA
[  179.092449] ata4.00: cmd c8/00:08:d8:32:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  179.092522] ata4.00: status: { DRDY ERR }
[  179.092543] ata4.00: error: { ICRC ABRT }
[  179.092571] ata4: soft resetting link
[  179.264231] ata4.00: configured for MWDMA2
[  179.264245] ata4: EH complete
[  179.291855] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  179.291896] ata4.00: BMDMA stat 0x26
[  179.291917] ata4.00: failed command: READ DMA EXT
[  179.291945] ata4.00: cmd 25/00:00:e0:0c:be/00:01:19:00:00/e0 tag 0 dma 131072 in
[  179.292039] ata4.00: status: { DRDY ERR }
[  179.292060] ata4.00: error: { ICRC ABRT }
[  179.292090] ata4: soft resetting link
[  179.464228] ata4.00: configured for MWDMA2
[  179.464241] ata4: EH complete
[  179.512748] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  179.512792] ata4.00: BMDMA stat 0x26
[  179.512815] ata4.00: failed command: READ DMA EXT
[  179.512843] ata4.00: cmd 25/00:00:e0:0d:be/00:01:19:00:00/e0 tag 0 dma 131072 in
[  179.512917] ata4.00: status: { DRDY ERR }
[  179.512938] ata4.00: error: { ICRC ABRT }
[  179.512966] ata4: soft resetting link
[  179.684225] ata4.00: configured for MWDMA2
[  179.684240] ata4: EH complete
[  179.700434] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  179.700473] ata4.00: BMDMA stat 0x26
[  179.700494] ata4.00: failed command: READ DMA EXT
[  179.700521] ata4.00: cmd 25/00:00:e0:0d:be/00:01:19:00:00/e0 tag 0 dma 131072 in
[  179.700595] ata4.00: status: { DRDY ERR }
[  179.700615] ata4.00: error: { ICRC ABRT }
[  179.700641] ata4: soft resetting link
[  179.872236] ata4.00: configured for MWDMA2
[  179.872252] ata4: EH complete
[  180.199133] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  180.199174] ata4.00: BMDMA stat 0x26
[  180.199195] ata4.00: failed command: READ DMA
[  180.199220] ata4.00: cmd c8/00:30:e0:19:9d/00:00:00:00:00/e9 tag 0 dma 24576 in
[  180.199299] ata4.00: status: { DRDY ERR }
[  180.199320] ata4.00: error: { ICRC ABRT }
[  180.199348] ata4: soft resetting link
[  180.368237] ata4.00: configured for MWDMA2
[  180.368251] ata4: EH complete
[  180.536754] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  180.536797] ata4.00: BMDMA stat 0x26
[  180.536821] ata4.00: failed command: READ DMA
[  180.536847] ata4.00: cmd c8/00:08:08:19:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  180.536939] ata4.00: status: { DRDY ERR }
[  180.536959] ata4.00: error: { ICRC ABRT }
[  180.536988] ata4: soft resetting link
[  180.708230] ata4.00: configured for MWDMA2
[  180.708242] ata4: EH complete
[  180.731496] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  180.731536] ata4.00: BMDMA stat 0x26
[  180.731557] ata4.00: failed command: READ DMA
[  180.731582] ata4.00: cmd c8/00:08:18:19:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  180.731655] ata4.00: status: { DRDY ERR }
[  180.731676] ata4.00: error: { ICRC ABRT }
[  180.731703] ata4: soft resetting link
[  180.900303] ata4.00: configured for MWDMA2
[  180.900322] ata4: EH complete
[  209.780320] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  209.780364] ata4.00: BMDMA stat 0x26
[  209.780386] ata4.00: failed command: READ DMA
[  209.780415] ata4.00: cmd c8/00:08:30:1e:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  209.780490] ata4.00: status: { DRDY ERR }
[  209.780512] ata4.00: error: { ICRC ABRT }
[  209.780542] ata4: soft resetting link
[  209.952237] ata4.00: configured for MWDMA2
[  209.952252] ata4: EH complete



```

---

### Post by newbie2244 on 2014-06-01
This   [http://www.wikihow.com/Fix-a-Cyclic-Redundancy-Check-Error](http://www.wikihow.com/Fix-a-Cyclic-Redundancy-Check-Error)  may be helpful.   Power losses can cause subsequent CRC errors.

Also,   [http://support.wdc.com/techinfo/general/errorcodes.asp](http://support.wdc.com/techinfo/general/errorcodes.asp)

Pls ignore the previous post if you do not have windows.

See ubuntu user anjohnso ' s comments in [http://ubuntuforums.org/archive/index.php/t-1034762.html](http://ubuntuforums.org/archive/index.php/t-1034762.html)

---

### Post by eclectik on 2014-06-02
Your quite right, many thanks for the reply.

I just executed a clean reboot and watched the boot log and it was all clean.

Many thanks.

---

