---
title: "have there been power consumption changes between 18.04 and 17.10"
date: 2018-05-03
forum: Hardware
---

### Post by jamie_le_notre on 2018-05-03
I have a 2018 xaiomi mi notebook pro, under 17.10 the power consumption was approx 3.5w (from powertop) now after doing a clean install of 18.04 power consumption is at 9.5w and the gpu fan is spinning constantly.

I've installed tlp and I've set cpu scaling to powersave

the Nvidia setting have been switched to integrated intel power save.

The fans on the Mi aren't pwm so I can reduce the speed of them.

Basically the usage of the laptop has dropped from 11 hours battery time (it was like that january to 18.04 release date) to 6 hours. and the fan noise is irritating, even with the tv on and the children scrapping with the daogs the fan is very noticeable.

I suspect its the NVidia gpu drivers not playing ball.

Any advice on how I can check and properly disable the nvidia gpu and just use the builtin intel

---

### Post by jamie_le_notre on 2018-05-03
solved,

intel_pstate=enable & thermald

---

