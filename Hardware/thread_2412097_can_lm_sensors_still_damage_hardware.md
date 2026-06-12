---
title: "can lm_sensors still damage hardware?"
date: 2019-02-08
forum: Hardware
---

### Post by Nader_Nooryani on 2019-02-08
[COLOR=#878A8C][FONT=IBMPlexSans][COLOR=#1A1A1B][FONT=&quot]I just ran lm_sensors and foolishly typed YES to everything.. This is a brand new PC I've built and I'm worried I've damaged something now.   Then I read that it can overwrite EEPROM and damage hardware from probing i2c.   This is a recent desktop chipset based on Intel series 300 (b360) with an i3-8100.  

Is lm_sensors still a risk?   I'm kinda freaking out here, how would I even know if something was damaged?
[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#878A8C][FONT=IBMPlexSans][FONT=inherit][FONT=inherit][FONT=inherit][/FONT][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by CatKiller on 2019-02-08
I always say yes to everything. I've never had a problem.

---

### Post by Nader_Nooryani on 2019-02-08
Have you selected YES to everything and on what hardware?  I mean my hardware seems to be working fine, but I wouldn't even know if it was messed up.

---

### Post by CatKiller on 2019-02-08
> **Nader_Nooryani said:**
> Have you selected YES to everything

> **CatKiller said:**
> I always say yes to everything.

>  and on what hardware? 

Everything I've wanted sensor output from.

>  I mean my hardware seems to be working fine, but I wouldn't even know if it was messed up.

You would know if it was messed up. Which means that it isn't.

sensors-detect works by poking everything with a stick and seeing what happens. If you're running it on a drone, or a robot, or some other embedded system, there may be things other than sensors on those buses, and they might not react in the expected way to being poked with a stick. That's why the warning's there.

On normal computers it's only sensors that use the inter-integrated circuit bus to communicate. I guess RGB lighting might, too. Everything important will use one of the higher-speed buses, like PCIe.

---

