---
title: "Acer TravelMate 4404WLMi Heating Under Edgy"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by wayward on 2006-10-29
Hello,

I have an issue with Edgy.  My Acer TravelMate 4404WLMi happily ran Breezy and Dapper, but with Edgy I'm experiencing random shutdowns when the CPU temperature shoots over 92-93-ish C.  I didn't bother to force it into yet another shutdown just to get the value straight, as AMD says my *Tdie* is 95C, and it shouldn't go over 85-86C anyhow.

Here's the breakdown of all the information I have:

[LIST]
[*]Dapper runs fine: userspace governor with powernowd will keep temperature under 85C.  I've noticed that whenever the temperature reaches that point, the CPU will temporarily slow down one step (1.8GHz -> 1.4GHz) for a second or so, giving itself time to cool down.  (I don't know what's responsible for this but I sure would like to know, as I haven't seen it happen under Edgy).
[*]Processor throttling is not supported under either Dapper or Edgy (/proc/acpi/processor/CPU0/throttling).  I did notice though that CPU0/states has one extra column (duration) under Edgy but I take it it's a new kernel feature.
[*]Neither Dapper or Edgy will recognize my fans.  /proc/acpi/fan/ is empty.  lm-sensors claims that my detected I/O chip (PC8739x) doesn't give any sensor info; might be the reason.  CPU fan does work though: it never goes off, at 73C it accelerates, and again at 83C.  This is both for Dapper and Edgy.
[*]Edgy overheats both with userspace/powernowd and ondemand governor.
[*]I have disabled APIC as it generated tons of errors and also some people have found that powernowd would not work with a broken APIC.  Nothing has changed for me, though -- Edgy still overheats.
[*]Edgy is running 2.6.17-10-generic kernel.  Modules loaded that might be of interest: cpufreq-*, dev_acpi, fan, i2c-core, i2c-ec, powernow-k8, processor, thermal
[*]sudo dmidecode [output]("http://paste.uni.cc/11176")
[*]sudo sensors-detect [output]("http://paste.uni.cc/11179")
[*]/proc/acpi/thermal_zone/TZS0/* [contents]("http://paste.uni.cc/11180").  Cooling mode is set to passive and can't be changed.
[/LIST]
If you know there's something that I've missed and is worth a shot, go ahead, at this point I'm willing to recompile the darned kernel just to try something new.

---

