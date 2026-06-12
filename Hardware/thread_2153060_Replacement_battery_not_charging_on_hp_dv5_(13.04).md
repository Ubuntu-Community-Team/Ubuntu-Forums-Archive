---
title: "Replacement battery not charging on hp dv5 (13.04)"
date: 2013-06-10
forum: Hardware
---

### Post by Greg314 on 2013-06-10
Hello there,

I just replaced my battery on my hp dv5-2144ca and 
[LIST=1]
[*]It is not charging, the charge constantly remains stuck around 20%,
[*]If I unplug the wire, the battery gives now power and the computer shuts down.
[/LIST]
My old battery works perfectly though.

I executed 
```
acpi -V
```
and here is what I get:
```
Battery 0: Unknown, 20%
Battery 0: design capacity 6513 mAh, last full capacity 6513 mAh = 100%
Adapter 0: on-line
Thermal 0: ok, 39.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 107.0 degrees C
Thermal 1: ok, 45.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 200.0 degrees C
Thermal 1: trip point 1 switches to mode hot at temperature 104.0 degrees C
Cooling 0: LCD 0 of 10
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 10
Cooling 3: Fan 1 of 1

```

A friend of mine told me to try to boot on Windows to check the battery status but I completely removed Windows from this computer and I have no dual boot.

Any idea ?

---

### Post by Greg314 on 2013-06-19
In order to test the thing, I have created a Win7 partition and flashed the BIOS to the latest version and... the situation is exactly the same.

The only improvement is that I now know that it is also the same under Win7: the battery appears but is not charging, and not powering neither. Therefore, it looks like a hardware issue.

Note that this battery is designed for a US/Canada PC (120V/60Hz) which I am using on a 220V/50Hz system. The AC adapter supposingly does the job but I wonder if the issue might come from there...

Any idea is still highly welcome !

---

