---
title: "mbmon output"
date: 2009-07-05
forum: Hardware
---

### Post by ajgreeny on 2009-07-05
In my BIOS I have overclocked my sempron 2400+ from 166Mhz to 200Mhz, with no apparent ill efects.  I installed lm-sensors, but that did nothing and would not show any thing at all, with no sensors detected even after probing the system. I therefore installed mbmon which works fine, though I'm not sure exactly what the output means in detail, and can find no info in the man, or on google about it.

I get
```
Temp.= 34.0, 25.0, 30.0; Rot.= 6308, 4017,    0
Vcore = 1.63, 1.63; Volt. = 3.38, 4.89, 11.55, -10.57, -4.56
```which seems OK to me but I don't know what the Rot.= is about; I presume perhaps the cooling fans.  Also what are the negative voltages for?

Any clues anyone, together with any comments about the temps showing.  They seem pretty low to me for an overclocked cpu, but I'm sure many know more about this than I do.

---

### Post by SteveDee on 2009-07-06
> **ajgreeny said:**
> In my BIOS I have overclocked my sempron 2400+ from 166Mhz to 200Mhz, with no apparent ill efects.  I installed lm-sensors, but that did nothing and would not show any thing at all, with no sensors detected even after probing the system. I therefore installed mbmon which works fine, though I'm not sure exactly what the output means in detail, and can find no info in the man, or on google about it.

I get
```
Temp.= 34.0, 25.0, 30.0; Rot.= 6308, 4017,    0
Vcore = 1.63, 1.63; Volt. = 3.38, 4.89, 11.55, -10.57, -4.56
```which seems OK to me but I don't know what the Rot.= is about; I presume perhaps the cooling fans.  Also what are the negative voltages for?

Any clues anyone, together with any comments about the temps showing.  They seem pretty low to me for an overclocked cpu, but I'm sure many know more about this than I do.

If you have some kind of "health" or "H/W Monitor" screen in your BIOS I suggest you note the values then compare with mbmon when in Ubuntu, as you can't be sure that mbmon or im-sensors is giving the correct temps (e.g. may be using the wrong driver or something). You also need to determine which temp(s) is cpu and which is the enclosure temp.

I agree that "rot" looks like the cpu and chassis fan rpm.

The negative temps are the -5V and -12V supplies (both of which look low to me).

One of our 4 computers has an AMD Sempron (I can't get im-sensors to work on this either, but it works fine of the other 3). Typical BIOS readings:-
System temp: 34degC
cpu: 40C

---

