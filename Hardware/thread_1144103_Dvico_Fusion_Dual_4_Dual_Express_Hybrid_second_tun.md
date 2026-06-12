---
title: "Dvico Fusion Dual 4 Dual Express Hybrid second tuner not working"
date: 2009-04-30
forum: Hardware
---

### Post by jtroybailey on 2009-04-30
[COLOR=black]Hi,

I have a Dvico Fusion Dual 4 Dual Express Hybrid tv tuner. It had been working fine in Mythbuntu 9.04 after i copied the firmware drivers across. After a reboot the second tuner stopped working. I deleted the channel list and scanned again. the signal was at 0% though the signal/noise ratio was at 98%. The scan found nothing. dmesg show the following:

[  805.948909] xc2028 1-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  805.950981] xc2028 1-0061: i2c output error: rc = -5 (should be 64)
[  805.950987] xc2028 1-0061: -5 returned from send
[  805.950993] xc2028 1-0061: Error -22 while loading base firmware
[  806.004044] xc2028 1-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  806.006119] xc2028 1-0061: i2c output error: rc = -5 (should be 64)
[  806.006123] xc2028 1-0061: -5 returned from send
[  806.006126] xc2028 1-0061: Error -22 while loading base firmware
[  806.008987] zl10353: write to reg 62 failed (err = -5)!
[  806.011026] zl10353: write to reg 5f failed (err = -5)!
[  806.013100] zl10353: write to reg 71 failed (err = -5)!
[  806.015148] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.017231] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.019269] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.021360] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.023401] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.025486] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.052656] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.054702] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.056799] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.058883] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.060964] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.063002] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.065078] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.067120] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.069199] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.096601] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.098684] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.100730] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.103314] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.105380] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.107420] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.109519] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.111562] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.113679] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.141017] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.143058] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.145136] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.147351] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.149552] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.151615] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.153712] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.155819] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.157932] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.185325] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.187389] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.189485] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.191552] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.193650] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.195759] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.197870] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.199937] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.202037] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.229398] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.231462] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.233557] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.235624] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.237739] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.239836] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.241943] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.244026] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.246135] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.273612] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.275675] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.277737] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.280430] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.282496] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.284558] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.287169] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.289241] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.291682] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.319035] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.321125] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.323237] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.325359] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.327585] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.329683] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.331751] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.333877] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.335976] zl10353_read_register: readreg error (reg=21, ret==-5)
[  806.363453] zl10353_read_register: readreg error (reg=6, ret==-5)
[  806.365571] zl10353_read_register: readreg error (reg=10, ret==-5)
[  806.367634] zl10353_read_register: readreg error (reg=11, ret==-5)
[  806.369744] zl10353_read_register: readreg error (reg=16, ret==-5)
[  806.372616] zl10353_read_register: readreg error (reg=17, ret==-5)
[  806.374679] zl10353_read_register: readreg error (reg=18, ret==-5)
[  806.376785] zl10353_read_register: readreg error (reg=19, ret==-5)
[  806.378887] zl10353_read_register: readreg error (reg=20, ret==-5)
[  806.380984] zl10353_read_register: readreg error (reg=21, ret==-5)
[  807.014069] zl10353: write to reg 50 failed (err = -5)!
[  816.359427] zl10353_read_register: readreg error (reg=80, ret==-5)
[  816.361644] zl10353: write to reg 50 failed (err = -5)!

It was working till after i rebooted. before i rebooted i had install updates which were cups and firefox. what do you guys think?

Thanks, Jamie
[/COLOR]

---

