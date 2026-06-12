---
title: "Dell Inspiron 1501 Fan Control Issues"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by Arenlor on 2007-07-04
I have a two speed fan on here and it works fine in the system test and in Windows Vista, which Vista is messed up rather badly with it so I'm surprised at that. The issue is in Ubuntu the fan won't always start up and when it does it only goes into the low mode, even though I've hit temperatures of 60 and above without it kicking it, it usually runs around 50 if it's not on and 38 when it rarely turns on. Is there a quickfix or am I gonna have to spend more ungodly time on this machine to make it work. Which brings up the question of why is Dell selling Linux if their machines hardly work in it? Maybe Microsoft hired them so that people will hate Linux since it doesn't work?

---

### Post by Arrdee on 2007-07-05
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)

Keep reading until you hit the heading "CPU". Should explain how to set up a program called GKrellm, which has done wonders for keeping my Dell's fan running. You can set the parameters with it, too, for when the fans turn on.

---

### Post by Arenlor on 2007-07-07
I tired following the instructions but it didn't work.

---

### Post by Arrdee on 2007-07-08
How doesn't it work? The fans aren't being controlled, you're getting error messages...?

---

