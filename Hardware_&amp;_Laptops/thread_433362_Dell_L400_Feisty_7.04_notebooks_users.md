---
title: "Dell L400 Feisty 7.04 notebooks users"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by jgcamp99 on 2007-05-04
Very important ACPI and temperature behavior tip. Battery calibration using the bios calibration & learning tool, seems to have significantly improved operation under Ubuntu 7.04 Feisty. Operation thru 55% of battery life usage has yet to go over 50* C for the cpu and 42* C for hdd.

Dell indicates periodic calibrations be performed to account for changes in battery conditioning. I had never done it after installing Edgy and later upgrading to Feisty. In the past couple of days, I had seen cpu temps approach consistently higher temps @ 65-70* C cpu & 48-50* C hdd. It would lock up and take some cooling off time before it would recognize the hdd and boot into Ubuntu.  

Perhaps this improves your temperature experiences as well ?

---

### Post by jgcamp99 on 2007-05-06
Battery calibration worked for only a few battery cycles, it's back to running hotter again. It hasn't reached the point where it locks up and shuts down, but I fear that's a battery cycle or two away from starting to recurr.

Well, time to go back to researching ACPI/APM.

---

### Post by jgcamp99 on 2007-05-08
Hmmm, talking to myself here. Anyway, I'm convinced ACPI works to some extent. Everytime I try to put an applet for cpu frequency scaling, it denies me the satisfaction that throttling the cpu is supported.

So my next thought process is the Thermal Zone. The fan kicks on at 65* C, and that is what it's set at in that /proc/acpi/thermal_zone/THRM/trip_points file. Anyway to change the value from 65 to say 45* C, if it's even possible for a more permanent and proper adjustment ? I know the fan would come on more often, but the heat from it stays in so long that it also drives up the temp on the hdd. I figure the hdd does generate it's share of heat, but not 65* C hot, as it's never gotten over 50* C itself. It would be nice to have a program that you could set the trip points manually if need be to adjust it permanently. I'd hate to have to try to trick it by setting the sensors to think it is running warmer than it is using the offset in preferences. I don't know whether that would even work, setting the offset up by 20 degreees to fool it, even though the fan kicked on and the isual said 65, when it was really 45* C simply is an inaccuracy in temp reading. That's why I'm curious as to whether it can be done in the trip_points file. I'd hope the fan would vacate the slimmer profile of heat way before it gets to the true 65* C temp ?

---

### Post by walopower on 2008-04-21
Unfortunately Ubuntu 6.06 LTS was only release that works for me.
in 7.10, manually cpu-freq works, suspend works, but network must restart. Fan works with bios A03, but sometimes fan not start at all. Standby get display blank, but sometimes backlith comes back up after a while, but screen if still "black".

---

