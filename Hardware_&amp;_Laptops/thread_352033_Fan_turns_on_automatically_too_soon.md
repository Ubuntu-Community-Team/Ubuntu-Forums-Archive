---
title: "Fan turns on automatically too soon"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by davidY on 2007-02-02
Hi, I own a dell laptop (Inspiron 6400 to be precise), and I have successfully installed edgy and i8k module. Now the fans just turn on the moment the temperature reaches 45 degrees. While this is probably alright, it turns out that the laptop temperature stabalises at 45 degrees from past experience. So I would prefer that the fans turn on at something like 48 degrees. Also the fans only turn off once they reach 30 degrees. This takes a long amount of time. 

I have tried everything to change what seems like the default fan activity. I am not sure if it is the bios or linux that is doing it, but everytime I use i8k to stop the fan, within a few seconds, the fans start up again, so I think it is possibly another part of linux changing the fan speeds, or the bios. 

Is there a way to change the fan action?

---

### Post by kairu0 on 2007-02-02
Normally, this would be a bios setting. Have you checked the bios yet?

---

### Post by davidY on 2007-02-03
The bios does not give specific places to change the fan operation. Only hdd operation mode from normal to quiet.

---

### Post by RandomJoe on 2007-02-03
IIRC, i8k uses built-in default setpoints when first installed.  You can change those by creating an /etc/i8kmon file.  The formatting of this file is in the manpage ('man i8kmon' I think - not using my laptop right now!) and this is what I use on my Dell Latitude C840:
```
set config(0) {{0 0} -1 53 -1 53}
set config(1) {{0 1} 38 60 38 60}
set config(2) {{1 1} 54 71 54 71}
set config(3) {{2 2} 60 128 60 128}
```
Basically, config[0] is the "off" state, config[1] is "one fan on" (assuming your machine has two - most do, even if the second is buried inside somewhere) and you can tell it which fan is first on by swapping {0 1} for {1 0}.  config(2) is "both on low" and config[3] is "both on high".  The temps are in degC.

The numbers mean "when in this state, if the temp exceeds this high temp, jump to the next state".  And the other way "when in this state, if it drops below this low temp, drop down".  Which is why the all-off state has -1 (unreachable) and all-high has 128 (sure hope it's unreachable!).

If you only have one fan (I've only had one very small Dell have only one fan) you just have three configs (0,1,2).  The man page discusses this.

---

