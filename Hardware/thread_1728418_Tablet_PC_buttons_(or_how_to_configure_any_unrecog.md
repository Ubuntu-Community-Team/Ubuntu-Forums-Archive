---
title: "Tablet PC buttons (or how to configure any unrecognized button)?"
date: 2011-04-13
forum: Hardware
---

### Post by AZorin on 2011-04-13
I'm currently trying to set up the extra buttons on my Tablet PC and I can't find a way how to get a working button code to show up. I have used the xev command and it doesn't show up anything when I press the buttons. When I tried the dmesg command I get this:
```
[  520.273409] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  520.273418] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  520.499423] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  520.499433] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  520.992880] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  520.992889] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  521.209819] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  521.209832] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  521.358197] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  521.358207] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  521.505726] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  521.505736] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  521.782427] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  521.782437] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  521.930513] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  521.930522] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  522.009454] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  522.009463] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  522.157582] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  522.157592] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  522.236852] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  522.236862] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  522.315543] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  522.315552] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  522.394259] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  522.394269] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  522.542348] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  522.542358] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  522.622056] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  522.622066] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  522.769640] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  522.769650] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  531.024764] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  531.024773] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  531.176222] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  531.176232] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  531.466929] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  531.466938] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  531.615016] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  531.615025] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  531.693959] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  531.693969] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  531.842085] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  531.842095] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  531.921069] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  531.921079] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  532.000083] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  532.000093] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  532.079455] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  532.079464] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  532.157741] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  532.157750] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  532.236995] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  532.237005] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  532.315966] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  532.315976] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  532.394912] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  532.394922] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  532.473929] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  532.473939] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  532.552873] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  532.552883] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  532.631890] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  532.631900] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  532.710834] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  532.710844] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  532.789849] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  532.789858] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  532.937941] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  532.937951] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  533.016651] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  533.016661] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  533.095910] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  533.095919] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  533.174841] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  533.174851] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  533.253864] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  533.253874] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  533.332577] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  533.332587] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  533.411787] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  533.411797] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  533.490806] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  533.490816] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  533.569748] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  533.569758] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  533.648764] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  533.648773] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  533.727710] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  533.727719] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  533.875834] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  533.875844] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  533.954812] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  533.954822] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  534.033527] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  534.033537] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  534.517550] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  534.517560] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  534.596489] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  534.596499] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  534.675512] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  534.675522] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  534.823599] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  534.823609] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  534.902831] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  534.902841] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  534.981559] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  534.981568] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  535.060274] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  535.060283] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  535.139527] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  535.139537] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  535.287573] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  535.287583] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  535.366322] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  535.366332] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  535.445531] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  535.445541] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  535.593658] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  535.593668] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  535.672633] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  535.672642] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  535.751620] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  535.751630] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  535.899709] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  535.899719] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  535.978649] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  535.978658] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  536.057950] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  536.057959] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  536.136651] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  536.136660] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  536.284702] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  536.284712] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  536.363718] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  536.363728] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  536.442432] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  536.442441] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  536.521638] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  536.521648] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  536.669770] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  536.669780] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  536.748742] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  536.748752] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  536.827732] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  536.827742] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  536.906702] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  536.906712] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  539.115824] show_signal_msg: 15 callbacks suppressed
[  539.115838] xbindkeys-confi[2037]: segfault at 1 ip 0804d398 sp bfeace60 error 4 in xbindkeys-config[8048000+a000]
[  837.770783] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  837.770793] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  837.989935] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  837.989944] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  838.138023] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  838.138033] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  838.286338] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  838.286348] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  838.434427] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  838.434437] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  838.582516] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  838.582526] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  838.661533] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  838.661543] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  838.740478] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  838.740487] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  838.888606] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  838.888616] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  838.967577] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  838.967586] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  839.046566] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  839.046576] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  839.194390] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  839.194399] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  839.422063] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  839.422073] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  839.569816] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  839.569826] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  839.648801] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  839.648811] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  839.796887] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  839.796897] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  839.875830] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  839.875839] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  839.954847] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  839.954857] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  840.102675] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  840.102685] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  840.182206] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  840.182216] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  840.330298] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  840.330308] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  840.408723] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  840.408732] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  840.487970] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  840.487980] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  840.566909] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  840.566919] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  840.715040] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  840.715049] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  840.794012] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  840.794022] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  840.873293] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  840.873302] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  840.951973] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  840.951983] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  841.030964] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  841.030973] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  841.179050] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  841.179060] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  841.258494] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  841.258504] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  841.336745] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  841.336755] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  841.415729] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  841.415738] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  841.495296] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  841.495305] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  841.573956] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  841.573965] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  841.722040] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  841.722049] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  841.800988] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  841.800997] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  841.880000] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  841.880011] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  842.028099] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  842.028109] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  842.107072] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  842.107082] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  842.185790] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  842.185800] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  842.333876] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  842.333886] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  842.413126] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  842.413136] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  842.492373] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  842.492383] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  842.640196] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  842.640205] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  842.719132] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  842.719142] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  842.867225] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  842.867234] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  842.946533] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  842.946543] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  843.025187] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  843.025197] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  843.104203] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  843.104212] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  843.252031] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  843.252041] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  843.331009] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  843.331019] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  843.479100] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  843.479110] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  843.558344] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  843.558353] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  843.637321] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  843.637330] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  843.716304] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  843.716314] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  843.923628] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  843.923638] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  844.071716] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  844.071725] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  844.220235] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  844.220244] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  844.368353] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  844.368363] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  844.446613] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  844.446622] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  844.525591] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  844.525600] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  844.673942] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  844.673952] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  844.752886] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  844.752895] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  844.901016] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  844.901025] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  844.979996] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  844.980006] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  845.058977] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  845.058986] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  845.207067] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  845.207077] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  845.286328] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  845.286338] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  845.364760] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  845.364770] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  845.443742] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  845.443751] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  845.592060] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  845.592069] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  845.671038] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  845.671048] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  845.819128] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  845.819137] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  845.898146] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  845.898156] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  845.977088] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  845.977098] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  846.125219] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  846.125229] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  846.204190] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  846.204200] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  846.500379] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  846.500389] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  846.648466] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  846.648475] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[  930.462830] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  930.462839] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  930.615700] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  930.615709] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  930.766178] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[  930.766188] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[  930.845918] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[  930.845928] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[  931.072955] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[  931.072965] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[  931.289922] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[  931.289932] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[ 1564.010209] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[ 1564.010218] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[ 1564.227078] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[ 1564.227088] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[ 1569.642243] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[ 1569.642252] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[ 1569.790369] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[ 1569.790379] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[ 1609.548051] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[ 1609.548061] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[ 1609.764974] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[ 1609.764984] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[ 1610.318068] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[ 1610.318077] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[ 1610.535263] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[ 1610.535272] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
[ 1690.537480] atkbd serio0: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[ 1690.537490] atkbd serio0: Use 'setkeycodes e070 <keycode>' to make it known.
[ 1690.754673] atkbd serio0: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0).
[ 1690.754683] atkbd serio0: Use 'setkeycodes e013 <keycode>' to make it known.
[ 1691.584014] atkbd serio0: Unknown key pressed (translated set 2, code 0xda on isa0060/serio0).
[ 1691.584024] atkbd serio0: Use 'setkeycodes e05a <keycode>' to make it known.
[ 1691.732097] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
[ 1691.732106] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.

```
I only pressed the two keys one after the other once and I got all this text. When I tried to map all of these "keys" using the recommended command it doesn't do anything. 
This is really annoying me as I have looked all over the internet at all the methods I could find but nothing works. I hope that someone can help me.
Thanks in advance.
AZorin

---

