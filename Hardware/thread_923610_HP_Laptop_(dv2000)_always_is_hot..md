---
title: "HP Laptop (dv2000) always is hot."
date: 2008-09-18
forum: Hardware
---

### Post by dgavenda on 2008-09-18
I can't get my laptop under 80C when idle.  When it's taxed, it'll top out around 100C.  Crazy.  I use a Dell laptop at work and even when taxed, it'll be around 70C.  

Here's the acpi from my HP laptop:

 $acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 82.0 degrees C
     Thermal 2: ok, 86.0 degrees C
    AC Adapter 1: on-line


I have tried installing the latest bios as suggested from other posts.  It's sitting on a desk without anything around it so air flow is not a problem.  

Any ideas?

Thx,
Dan

---

### Post by dgavenda on 2008-09-21
Anyone?

This was basically idle.  Nothing really taxing the cpu.

$ acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 80.0 degrees C
     Thermal 2: ok, 81.0 degrees C
  AC Adapter 1: on-line

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +80.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +80.0°C  (crit = +100.0°C)

---

### Post by mempman on 2008-10-24
Actually those computers have a known defect.  I have a hp pavillion dv2422ca, and I used to have my laptop get extremely hot, close to you temperatures.  Actually my GPU was running at 120degC+.  After a month or so of this behavior, my display stopped working altogether and I had ship my unit back to hp for free repairs.

Call hp yourself and discuss with them.

---

### Post by DemonBob on 2008-10-27
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us), sending mine back this week for the wifi issue.

---

### Post by starcannon on 2008-10-27
dv2600 here, yep they get toasty, be sure to blow some canned air through both directions on the cpu vents. You'll be amazed how much stuff gets in there, and how quickly it builds up. That will make it run a lot cooler. I still have no long term solution for ours though. Currently 1 core is at 151 F and the other is at 133 F, the nvidia 8400m gs gpu is at 138 F.

The wifi area gets very warm, almost hot to the touch.

---

