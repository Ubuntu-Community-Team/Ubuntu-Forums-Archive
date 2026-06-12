---
title: "Battery Indicator Acer TM803LMi, Ubuntu 6.10"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by DocMSK on 2006-11-24
Hello,

New to Linux, but have found some great people and advice on this forum to help me get up and running.

The problem I have is with the battery indicator. I have Ubuntu 6.10 (Edgy Eft) installed on my Acer Travelmate 803LMi. On the whole 6.10 has worked "out of the box".

The battery indicator seems to represent the correct percentage of power remaining but the time associated with the percentage is all wrong. For example, if I unplug the laptop after a full charge it sometimes says 3 minutes remaining. The time jumps all over the place as the battery discharges. I also seem to think I get less "hours" out of the battery now compared to when I ran WinXP on it.

APCI -V also tells me battery will never fully charge, why is that? It says charging at zero rate, but it _is_ charging the battery.

```

@Ubuntu:~$ acpi -V
     Battery 1: discharging, 13%,  remaining
     Thermal 1: ok, 38.0 degrees C
  AC Adapter 1: off-line

@Ubuntu:~$ acpi -V
     Battery 1: charging, 22%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 39.0 degrees C
  AC Adapter 1: on-line

```

I have searched these forums and the web and have not found a satisfactory answer. 

Any advice, or fixes would be appreciated.

Regards
Doc

---

### Post by DocMSK on 2007-01-06
*bump* Any help appreciated.

---

