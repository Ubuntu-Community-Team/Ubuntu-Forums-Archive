---
title: "[SOLVED] Psp won't mount with 8gb mem stick"
date: 2008-09-07
forum: Hardware
---

### Post by goathunter on 2008-09-07
hello
I  am trying to get my psp to connect to my hardy laptop.
I used to have no probs connecting with a 4gb mem stick in the psp it just auto mounted. Now I have an 8gb card which the psp works with fine but it won't connect to the laptop with the 8gb card. I go into usb mode on the psp but nothing happens on the laptop.

output of dmesg was

> [47642.091301] evdev: no more free evdev devices
[47642.091316] input: failed to attach handler evdev to device input385, error: -23
[47642.131847] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[47642.131862] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[47767.192105] input: b43-phy0 as /devices/virtual/input/input386
[47767.204786] evdev: no more free evdev devices
[47767.204802] input: failed to attach handler evdev to device input386, error: -23
[47767.244357] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[47767.244372] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[47890.747814] input: b43-phy0 as /devices/virtual/input/input387
[47890.760625] evdev: no more free evdev devices
[47890.760640] input: failed to attach handler evdev to device input387, error: -23
[47890.800332] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[47890.800347] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48015.861307] input: b43-phy0 as /devices/virtual/input/input388
[48015.874114] evdev: no more free evdev devices
[48015.874129] input: failed to attach handler evdev to device input388, error: -23
[48015.914740] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48015.914755] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48139.417165] input: b43-phy0 as /devices/virtual/input/input389
[48139.425942] evdev: no more free evdev devices
[48139.425957] input: failed to attach handler evdev to device input389, error: -23
[48139.465820] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48139.465860] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48264.527775] input: b43-phy0 as /devices/virtual/input/input390
[48264.543249] evdev: no more free evdev devices
[48264.543264] input: failed to attach handler evdev to device input390, error: -23
[48264.578663] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48264.578678] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48389.641202] input: b43-phy0 as /devices/virtual/input/input391
[48389.656766] evdev: no more free evdev devices
[48389.656781] input: failed to attach handler evdev to device input391, error: -23
[48389.692199] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48389.692214] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48513.196920] input: b43-phy0 as /devices/virtual/input/input392
[48513.208578] evdev: no more free evdev devices
[48513.208593] input: failed to attach handler evdev to device input392, error: -23
[48513.247898] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48513.247913] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48638.305256] input: b43-phy0 as /devices/virtual/input/input393
[48638.314083] evdev: no more free evdev devices
[48638.314099] input: failed to attach handler evdev to device input393, error: -23
[48638.353555] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48638.353571] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48761.857227] input: b43-phy0 as /devices/virtual/input/input394
[48761.869913] evdev: no more free evdev devices
[48761.869928] input: failed to attach handler evdev to device input394, error: -23
[48761.909279] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48761.909295] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[48886.970630] input: b43-phy0 as /devices/virtual/input/input395
[48886.983407] evdev: no more free evdev devices
[48886.983422] input: failed to attach handler evdev to device input395, error: -23
[48887.023186] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[48887.023201] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[21765.506731] input: b43-phy0 as /devices/virtual/input/input396
[21765.521050] evdev: no more free evdev devices
[21765.521060] input: failed to attach handler evdev to device input396, error: -23
[21765.555055] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[21765.555063] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49137.185526] input: b43-phy0 as /devices/virtual/input/input397
[49137.198444] evdev: no more free evdev devices
[49137.198460] input: failed to attach handler evdev to device input397, error: -23
[49137.239186] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49137.239200] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49260.741951] input: b43-phy0 as /devices/virtual/input/input398
[49260.750253] evdev: no more free evdev devices
[49260.750269] input: failed to attach handler evdev to device input398, error: -23
[49260.789950] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49260.789966] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49385.851496] input: b43-phy0 as /devices/virtual/input/input399
[49385.863225] evdev: no more free evdev devices
[49385.863242] input: failed to attach handler evdev to device input399, error: -23
[49385.902575] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49385.902590] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49509.403264] input: b43-phy0 as /devices/virtual/input/input400
[49509.419010] evdev: no more free evdev devices
[49509.419025] input: failed to attach handler evdev to device input400, error: -23
[49509.454773] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49509.454788] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49634.512164] input: b43-phy0 as /devices/virtual/input/input401
[49634.520540] evdev: no more free evdev devices
[49634.520556] input: failed to attach handler evdev to device input401, error: -23
[49634.560312] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49634.560327] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49758.065698] input: b43-phy0 as /devices/virtual/input/input402
[49758.076341] evdev: no more free evdev devices
[49758.076357] input: failed to attach handler evdev to device input402, error: -23
[49758.116784] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49758.116799] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[49883.177134] input: b43-phy0 as /devices/virtual/input/input403
[49883.189874] evdev: no more free evdev devices
[49883.189889] input: failed to attach handler evdev to device input403, error: -23
[49883.229655] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[49883.229670] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50006.733926] input: b43-phy0 as /devices/virtual/input/input404
[50006.745696] evdev: no more free evdev devices
[50006.745713] input: failed to attach handler evdev to device input404, error: -23
[50006.785111] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50006.785127] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50131.846581] input: b43-phy0 as /devices/virtual/input/input405
[50131.862248] evdev: no more free evdev devices
[50131.862264] input: failed to attach handler evdev to device input405, error: -23
[50131.898535] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50131.898551] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50256.960081] input: b43-phy0 as /devices/virtual/input/input406
[50256.971768] evdev: no more free evdev devices
[50256.971784] input: failed to attach handler evdev to device input406, error: -23
[50257.011119] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50257.011134] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50380.516013] input: b43-phy0 as /devices/virtual/input/input407
[50380.531571] evdev: no more free evdev devices
[50380.531587] input: failed to attach handler evdev to device input407, error: -23
[50380.566986] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50380.567001] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50505.628277] input: b43-phy0 as /devices/virtual/input/input408
[50505.641104] evdev: no more free evdev devices
[50505.641119] input: failed to attach handler evdev to device input408, error: -23
[50505.680666] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50505.680681] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50629.184122] input: b43-phy0 as /devices/virtual/input/input409
[50629.196911] evdev: no more free evdev devices
[50629.196927] input: failed to attach handler evdev to device input409, error: -23
[50629.236742] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50629.236757] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50754.297815] input: b43-phy0 as /devices/virtual/input/input410
[50754.306438] evdev: no more free evdev devices
[50754.306454] input: failed to attach handler evdev to device input410, error: -23
[50754.347130] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50754.347145] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[50877.845458] input: b43-phy0 as /devices/virtual/input/input411
[50877.854253] evdev: no more free evdev devices
[50877.854269] input: failed to attach handler evdev to device input411, error: -23
[50877.893985] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[50877.894001] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51002.951993] input: b43-phy0 as /devices/virtual/input/input412
[51002.963757] evdev: no more free evdev devices
[51002.963772] input: failed to attach handler evdev to device input412, error: -23
[51003.003248] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51003.003264] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51126.506803] input: b43-phy0 as /devices/virtual/input/input413
[51126.519594] evdev: no more free evdev devices
[51126.519610] input: failed to attach handler evdev to device input413, error: -23
[51126.558991] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51126.559007] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51251.616427] input: b43-phy0 as /devices/virtual/input/input414
[51251.629084] evdev: no more free evdev devices
[51251.629099] input: failed to attach handler evdev to device input414, error: -23
[51251.669787] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51251.669801] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51376.729927] input: b43-phy0 as /devices/virtual/input/input415
[51376.742575] evdev: no more free evdev devices
[51376.742590] input: failed to attach handler evdev to device input415, error: -23
[51376.783456] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51376.783472] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51500.282322] input: b43-phy0 as /devices/virtual/input/input416
[51500.294414] evdev: no more free evdev devices
[51500.294429] input: failed to attach handler evdev to device input416, error: -23
[51500.333769] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51500.333784] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51623.838989] input: b43-phy0 as /devices/virtual/input/input417
[51623.854204] evdev: no more free evdev devices
[51623.854219] input: failed to attach handler evdev to device input417, error: -23
[51623.889636] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51623.889650] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51748.957035] input: b43-phy0 as /devices/virtual/input/input418
[51748.971713] evdev: no more free evdev devices
[51748.971729] input: failed to attach handler evdev to device input418, error: -23
[51749.011464] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51749.011478] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51874.074352] input: b43-phy0 as /devices/virtual/input/input419
[51874.085240] evdev: no more free evdev devices
[51874.085255] input: failed to attach handler evdev to device input419, error: -23
[51874.124612] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51874.124626] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[51997.626564] input: b43-phy0 as /devices/virtual/input/input420
[51997.641029] evdev: no more free evdev devices
[51997.641044] input: failed to attach handler evdev to device input420, error: -23
[51997.680807] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[51997.680823] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52122.738554] input: b43-phy0 as /devices/virtual/input/input421
[52122.754527] evdev: no more free evdev devices
[52122.754542] input: failed to attach handler evdev to device input421, error: -23
[52122.790372] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52122.790387] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52246.293474] input: b43-phy0 as /devices/virtual/input/input422
[52246.306170] evdev: no more free evdev devices
[52246.306186] input: failed to attach handler evdev to device input422, error: -23
[52246.345632] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52246.345647] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52371.407056] input: b43-phy0 as /devices/virtual/input/input423
[52371.419671] evdev: no more free evdev devices
[52371.419687] input: failed to attach handler evdev to device input423, error: -23
[52371.460464] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52371.460479] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52496.517425] input: b43-phy0 as /devices/virtual/input/input424
[52496.529186] evdev: no more free evdev devices
[52496.529203] input: failed to attach handler evdev to device input424, error: -23
[52496.568529] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52496.568543] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[23369.505589] input: b43-phy0 as /devices/virtual/input/input425
[23369.518845] evdev: no more free evdev devices
[23369.518856] input: failed to attach handler evdev to device input425, error: -23
[23369.552830] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[23369.552840] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52746.769130] input: b43-phy0 as /devices/virtual/input/input426
[52746.784955] evdev: no more free evdev devices
[52746.784970] input: failed to attach handler evdev to device input426, error: -23
[52746.821298] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52746.821313] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52871.881052] input: b43-phy0 as /devices/virtual/input/input427
[52871.893868] evdev: no more free evdev devices
[52871.893884] input: failed to attach handler evdev to device input427, error: -23
[52871.933246] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52871.933260] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[52995.437589] input: b43-phy0 as /devices/virtual/input/input428
[52995.449676] evdev: no more free evdev devices
[52995.449692] input: failed to attach handler evdev to device input428, error: -23
[52995.489105] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[52995.489120] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53120.552020] input: b43-phy0 as /devices/virtual/input/input429
[53120.567188] evdev: no more free evdev devices
[53120.567204] input: failed to attach handler evdev to device input429, error: -23
[53120.603879] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53120.603894] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53245.660095] input: b43-phy0 as /devices/virtual/input/input430
[53245.672677] evdev: no more free evdev devices
[53245.672693] input: failed to attach handler evdev to device input430, error: -23
[53245.712532] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53245.712547] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53369.216692] input: b43-phy0 as /devices/virtual/input/input431
[53369.228511] evdev: no more free evdev devices
[53369.228528] input: failed to attach handler evdev to device input431, error: -23
[53369.267913] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53369.267928] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53492.772340] input: b43-phy0 as /devices/virtual/input/input432
[53492.788297] evdev: no more free evdev devices
[53492.788313] input: failed to attach handler evdev to device input432, error: -23
[53492.825145] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53492.825159] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53617.886321] input: b43-phy0 as /devices/virtual/input/input433
[53617.901816] evdev: no more free evdev devices
[53617.901832] input: failed to attach handler evdev to device input433, error: -23
[53617.937338] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53617.937353] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53742.995081] input: b43-phy0 as /devices/virtual/input/input434
[53743.003361] evdev: no more free evdev devices
[53743.003376] input: failed to attach handler evdev to device input434, error: -23
[53743.042634] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53743.042648] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53866.546561] input: b43-phy0 as /devices/virtual/input/input435
[53866.555175] evdev: no more free evdev devices
[53866.555190] input: failed to attach handler evdev to device input435, error: -23
[53866.594542] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53866.594556] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[53991.652038] input: b43-phy0 as /devices/virtual/input/input436
[53991.663746] evdev: no more free evdev devices
[53991.663762] input: failed to attach handler evdev to device input436, error: -23
[53991.703153] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[53991.703168] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54115.207721] input: b43-phy0 as /devices/virtual/input/input437
[54115.219539] evdev: no more free evdev devices
[54115.219555] input: failed to attach handler evdev to device input437, error: -23
[54115.258937] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54115.258952] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54240.321584] input: b43-phy0 as /devices/virtual/input/input438
[54240.333057] evdev: no more free evdev devices
[54240.333072] input: failed to attach handler evdev to device input438, error: -23
[54240.372299] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54240.372315] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54365.429984] input: b43-phy0 as /devices/virtual/input/input439
[54365.438579] evdev: no more free evdev devices
[54365.438596] input: failed to attach handler evdev to device input439, error: -23
[54365.478059] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54365.478074] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54488.978042] input: b43-phy0 as /devices/virtual/input/input440
[54488.990389] evdev: no more free evdev devices
[54488.990405] input: failed to attach handler evdev to device input440, error: -23
[54489.030083] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54489.030098] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54612.533638] input: b43-phy0 as /devices/virtual/input/input441
[54612.542211] evdev: no more free evdev devices
[54612.542227] input: failed to attach handler evdev to device input441, error: -23
[54612.581533] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54612.581548] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54737.644224] input: b43-phy0 as /devices/virtual/input/input442
[54737.659710] evdev: no more free evdev devices
[54737.659725] input: failed to attach handler evdev to device input442, error: -23
[54737.695512] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54737.695526] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54862.752706] input: b43-phy0 as /devices/virtual/input/input443
[54862.761253] evdev: no more free evdev devices
[54862.761270] input: failed to attach handler evdev to device input443, error: -23
[54862.800698] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54862.800713] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[54986.304440] input: b43-phy0 as /devices/virtual/input/input444
[54986.317054] evdev: no more free evdev devices
[54986.317069] input: failed to attach handler evdev to device input444, error: -23
[54986.356745] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[54986.356760] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55111.417889] input: b43-phy0 as /devices/virtual/input/input445
[55111.430553] evdev: no more free evdev devices
[55111.430568] input: failed to attach handler evdev to device input445, error: -23
[55111.470049] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55111.470064] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55234.970906] input: b43-phy0 as /devices/virtual/input/input446
[55234.986359] evdev: no more free evdev devices
[55234.986375] input: failed to attach handler evdev to device input446, error: -23
[55235.022149] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55235.022164] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55360.084326] input: b43-phy0 as /devices/virtual/input/input447
[55360.099864] evdev: no more free evdev devices
[55360.099879] input: failed to attach handler evdev to device input447, error: -23
[55360.135623] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55360.135637] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55483.640286] input: b43-phy0 as /devices/virtual/input/input448
[55483.655675] evdev: no more free evdev devices
[55483.655690] input: failed to attach handler evdev to device input448, error: -23
[55483.691485] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55483.691500] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55608.753634] input: b43-phy0 as /devices/virtual/input/input449
[55608.765207] evdev: no more free evdev devices
[55608.765222] input: failed to attach handler evdev to device input449, error: -23
[55608.804540] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55608.804555] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55732.308269] input: b43-phy0 as /devices/virtual/input/input450
[55732.321022] evdev: no more free evdev devices
[55732.321038] input: failed to attach handler evdev to device input450, error: -23
[55732.360366] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55732.360381] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55857.418288] input: b43-phy0 as /devices/virtual/input/input451
[55857.430518] evdev: no more free evdev devices
[55857.430534] input: failed to attach handler evdev to device input451, error: -23
[55857.471223] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55857.471238] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[55982.531453] input: b43-phy0 as /devices/virtual/input/input452
[55982.540049] evdev: no more free evdev devices
[55982.540065] input: failed to attach handler evdev to device input452, error: -23
[55982.579446] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[55982.579461] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[56106.112061] input: b43-phy0 as /devices/virtual/input/input453
[56106.123633] evdev: no more free evdev devices
[56106.123650] input: failed to attach handler evdev to device input453, error: -23
[56106.162558] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[56106.162573] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[28086.865832] usb 3-6: new high speed USB device using ehci_hcd and address 4
[28086.998795] usb 3-6: configuration #1 chosen from 1 choice
[28087.006441] scsi3 : SCSI emulation for USB Mass Storage devices
[28087.006990] usb-storage: device found at 4
[28087.006995] usb-storage: waiting for device to settle before scanning
[28092.310390] usb-storage: device scan complete
[28092.311207] scsi 3:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[28092.326284] sd 3:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[28092.326776] sd 3:0:0:0: [sdc] Write Protect is off
[28092.326780] sd 3:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[28092.326784] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[28092.329539] sd 3:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[28092.330022] sd 3:0:0:0: [sdc] Write Protect is off
[28092.330026] sd 3:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[28092.330031] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[28092.330038]  sdc: sdc1
[28092.331767] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[28092.331818] sd 3:0:0:0: Attached scsi generic sg3 type 0
[56271.284241] usb 3-6: USB disconnect, address 4
[56307.642447] input: b43-phy0 as /devices/virtual/input/input454
[56307.652942] evdev: no more free evdev devices
[56307.652959] input: failed to attach handler evdev to device input454, error: -23
[56307.692430] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[56307.692445] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[56312.164325] usb 3-6: new high speed USB device using ehci_hcd and address 5
[56312.298536] usb 3-6: configuration #1 chosen from 1 choice
[56312.362018] scsi4 : SCSI emulation for USB Mass Storage devices
[56312.371942] usb-storage: device found at 5
[56312.371953] usb-storage: waiting for device to settle before scanning
[56318.901528] usb-storage: device scan complete
[56318.902636] scsi 4:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[56318.919466] sd 4:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[56318.922843] sd 4:0:0:0: [sdc] Write Protect is off
[56318.922853] sd 4:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[56318.922859] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[56318.929335] sd 4:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[56318.929954] sd 4:0:0:0: [sdc] Write Protect is off
[56318.929962] sd 4:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[56318.929967] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[56318.929979]  sdc: sdc1
[56318.931608] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[56318.931698] sd 4:0:0:0: Attached scsi generic sg3 type 0
[28247.113897] input: b43-phy0 as /devices/virtual/input/input455
[28247.124919] evdev: no more free evdev devices
[28247.124931] input: failed to attach handler evdev to device input455, error: -23
[28247.163456] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[28247.163466] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[25170.638745] usb 3-6: USB disconnect, address 5
[25203.712311] input: b43-phy0 as /devices/virtual/input/input456
[28354.199981] evdev: no more free evdev devices
[28354.199991] input: failed to attach handler evdev to device input456, error: -23
[28354.232015] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[28354.232025] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[56892.116201] input: b43-phy0 as /devices/virtual/input/input457
[56892.127413] evdev: no more free evdev devices
[56892.127429] input: failed to attach handler evdev to device input457, error: -23
[56892.167295] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[56892.167309] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[56912.542676] usb 3-6: new high speed USB device using ehci_hcd and address 6
[56912.675648] usb 3-6: configuration #1 chosen from 1 choice
[56912.740393] scsi5 : SCSI emulation for USB Mass Storage devices
[56912.746122] usb-storage: device found at 6
[56912.746132] usb-storage: waiting for device to settle before scanning
[25278.842952] usb-storage: device scan complete
[25278.843692] scsi 5:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[25278.859556] sd 5:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[25278.860787] sd 5:0:0:0: [sdc] Write Protect is off
[25278.860794] sd 5:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[25278.860797] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[25278.863389] sd 5:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[25278.864142] sd 5:0:0:0: [sdc] Write Protect is off
[25278.864148] sd 5:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[25278.864151] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[25278.864158]  sdc: sdc1
[25278.869523] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[25278.869979] sd 5:0:0:0: Attached scsi generic sg3 type 0
[25342.256032] input: b43-phy0 as /devices/virtual/input/input458
[25342.264456] evdev: no more free evdev devices
[25342.264469] input: failed to attach handler evdev to device input458, error: -23
[25342.303260] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[25342.303270] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).


I believ this is the part relative to the psp

> [28092.310390] usb-storage: device scan complete
[28092.311207] scsi 3:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[28092.326284] sd 3:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[28092.326776] sd 3:0:0:0: [sdc] Write Protect is off
[28092.326780] sd 3:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[28092.326784] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[28092.329539] sd 3:0:0:0: [sdc] 16220160 512-byte hardware sectors (8305 MB)
[28092.330022] sd 3:0:0:0: [sdc] Write Protect is off
[28092.330026] sd 3:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[28092.330031] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[28092.330038]  sdc: sdc1
[28092.331767] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[28092.331818] sd 3:0:0:0: Attached scsi generic sg3 type 0
[56271.284241] usb 3-6: USB disconnect, address 4
[56307.642447] input: b43-phy0 as /devices/virtual/input/input454
[56307.652942] evdev: no more free evdev devices


any help would be appriciated

thankyou for your time.

---

### Post by goathunter on 2008-09-08
tried this > marcus@marcus-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/psp -o iocharset=utf8,umask=000
mount: /dev/sdb1 already mounted or /media/psp busy
mount: according to mtab, /dev/sdb1 is mounted on /media/disk
marcus@marcus-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   42G  9.6G  82% /
varrun                220M  120K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   68K  220M   1% /dev
devshm                220M   12K  220M   1% /dev/shm
lrm                   220M   39M  181M  18% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       55G   42G  9.6G  82% /home/marcus/.gvfs
/dev/sdb1             294G  279G  226M 100% /media/disk


but as you can see no result.

---

### Post by Echodown on 2008-09-08
if the memory stick is formatted for NTFS, a format the is preferred and only used on windows systems, then it will not load. Can't remember how to format the psps memory stick to different formats. 

when you do learn that, ext3 is the best format to use in tandum with ubuntu.

---

### Post by goathunter on 2008-09-08
hello yeah it works fine on my mates windows laptop. Whats strange is that my 4gb mem stick is detected fine and it was formatted on the psp the same way the 8gb one was.

tried this as well  > marcus@marcus-laptop:~$ 
marcus@marcus-laptop:~$ sudo fdisk -l
[sudo] password for marcus: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7132    57287758+  83  Linux
/dev/sda2            7133        7296     1317330    5  Extended
/dev/sda5            7133        7296     1317298+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042464

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 8304 MB, 8304721920 bytes
255 heads, 63 sectors/track, 1009 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1008     8096728+   b  W95 FAT32
marcus@marcus-laptop:~$ 



so its being detected, just showing up where I can do anything with it.

---

### Post by goathunter on 2008-09-08
problem solved. I copied the files from the memory stick that worked onto a flash drive. I then copied them onto my mates winxp laptop. The hooked the psp up to the winxp and deleted every file on the memstik that wasn't connecting. The copied the files from the working one to it. Now it connects fine.
cheers

---

