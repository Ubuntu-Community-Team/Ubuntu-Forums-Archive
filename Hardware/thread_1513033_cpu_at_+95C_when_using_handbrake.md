---
title: "cpu at +95C when using handbrake"
date: 2010-06-18
forum: Hardware
---

### Post by Gryphen on 2010-06-18
When I use handbrake on my laptop it reaches 93-100+C. Will this damage my cpu? I've done 50+ encodes already and it's not dead yet.

---

### Post by Yellow Pasque on 2010-06-18
If that is the actual CPU temp, then yes, you will eventually damage your CPU. Now would be a good time to clean out the laptop internals and possibly reseat the heatsink.

---

### Post by Linuxforall on 2010-06-18
Technically all modern CPUs shut off at dangerous lvel which is usually 78C for its core, its hard coded and most motherboard BIOS supports that, they also resort to underclocking first so I am not sure whether 95C is your actual temp as in that case it means your CPU should be fried already.

---

### Post by Yellow Pasque on 2010-06-18
Perhaps you're seeing the GPU temp, and 95C is not so bad (but still a bit warm).

---

### Post by Gryphen on 2010-06-19
This in what the "sensors" command prints:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +99.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +105.0°C, crit = +105.0°C)

The two coretemp ones don't seem to change, I know that it will shutdown if it overheats because my sister has crashed it by playing games while it's on the couch.

BTW my processor is a Intel pentium dual-core T4200

---

### Post by Gryphen on 2010-06-19
> **Temüjin said:**
> If that is the actual CPU temp, then yes, you will eventually damage your CPU. Now would be a good time to clean out the laptop internals and possibly reseat the heatsink.
When it's idle it's about 50-60C which doesn't seem that bad. Would useing a high quality thermal compound like arctic silver help? And while not as good as taking it apart and cleaning it I've used a air duster to clean it, Which wouldn't really do a good job removing all the cat hair thats probably in there!

---

### Post by Yellow Pasque on 2010-06-19
AS could help if you're really idling near 60C, but as Linuxforall said, if your CPU was actually at 95C under load, it would probably be fried by now.

---

### Post by Gryphen on 2010-06-19
I took my computer apart and unlike my moms computer which has a fan access panel I had to completely dismantle it to get to the fan. Now it idles at 45-50C and when the cpu is 100% in use it stay around 64C, And I also have an extra screw now!!

---

### Post by Gryphen on 2010-06-19
Is there a way to check for minor cpu damage?

---

