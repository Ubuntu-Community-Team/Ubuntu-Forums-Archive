---
title: "fan control of ga-p35 and chilltec"
date: 2008-08-18
forum: General Help
---

### Post by kcavagnolo on 2008-08-18
I've moved into a very quite office, so a previously inconsequential problem has developed into a huge irritation:

When idle or under normal use my CPU fan will be running at 2400 rpm, every 15 seconds the fan starts to slow down, then ~2 seconds later it revs back up to 2400 rpm. The up and down is driving me crazy.

I've scoured the internet looking for answers and nothing has worked thus far.

-- lmsensors is installed correctly and working
-- sensors returns correct information about temps and rpms even though I'm using it8718-isa-0290 and no entry in sensors.conf is meant for this adapter
-- pwmconfig detects all devices but cannot stop or control the fans
-- I've tried every combination of autofan "enabled" and "auto", "pwm", and "voltage" in the BIOS and nothing takes
-- disabling autofan in the BIOS does not alleviate the problem either

Here is my setup:
Gigabyte GA-P35-DS4
Ultra Chilltec (yep, it's plugged into the CPU_FAN mobo pins)
Ubuntu Hardy Heron
it8718-isa-0290 adapter

Advice?

---

### Post by kcavagnolo on 2008-12-08
I'm updating this for the purposes of creating a resource that someone else may want someday were they to Google for "chilltec up down"

After much struggle, I talked to a "parts" person at Ultra. The annoying up and down cyclic behavior of the fan is a "feature." Which to me means, "We wrote crap software and the temp probe is a piece of shiat so the fan throttles all the time."

There is no fix for this, except taking the Chilltec out of your computer and throwing it away.

---

