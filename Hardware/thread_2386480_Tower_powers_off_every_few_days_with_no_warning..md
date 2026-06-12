---
title: "Tower powers off every few days with no warning."
date: 2018-03-06
forum: Hardware
---

### Post by Adam_GUI on 2018-03-06
I have my main tower running XUbuntu 16.04.
Every few days, the machine will power down with no warning.
It doesn't do a safe shutdown.  It just stops.  Fans spin down, lights go out on the tower.

It started doing this when trying to burn a DVD ROM.  But, now it does this seemingly every few days with no warning.

At first, I thought this was the power supply.
So, that got changed out.  Including moving cases so that the supply could reach everything.
That means everything got dusted out during the move.

Next I thought it may be the power strip.
That was changed.  No change in behavior.
Nothing else on the strip tends to blink or shut down like the tower does.

I'm thinking temperature may be an issue.

Neither hard disk clicks, so, I don't think it's drive failure.

In earlier versions of ubuntu, I remember there being a desklet app for CPU temperature monitoring.
I can't remember what it was called or how to find it.

Any ideas on stuff I could have missed?
Is there a recommended app for drive health?

Is there a setting to keep fans spinning for maximum cool down?

---

### Post by Yellow Pasque on 2018-03-06
> Is there a setting to keep fans spinning for maximum cool down? 

Probably, in your BIOS. You didn't even tell us the model, so I can't be more specific.

> I'm thinking temperature may be an issue.

Have you looked at output of sensors command? Are you using any kind of temp monitor to see what the CPU temp gets to under load? Have you dusted out the heatsink/fans lately?

---

### Post by Autodave on 2018-03-06
*psensor *is a program that will monitor that.  Another possibility is a RAM chip failing. GENERALLY it would be the one in the first slot, assuming you have more than one RAM chip installed. But, it could be any of them.  If you have more than one, remove the one in the first slot and move another one into that position.  Try it without that chip in and see if it continues to run. If not, put that one back in  and leave a different one out. Keep doing that until you have tried it with each chip out or until you don't have the problem anymore.

---

### Post by Yellow Pasque on 2018-03-06
I'd run memtest before physically messing with the RAM modules. I've never encountered a bad RAM module shutting the computer down as sole symptom. Usually, a bad module will cause strange errors/crashes, or if the mobo doesn't like the module, the system won't boot.

---

### Post by rbmorse on 2018-03-07
A RAM module in which overheating causes the a short on the vDIMM traces in the socket will cause an ATX power supply to invoke short circuit protection and shut down instantly.  It's very rare, but I have seen it happen. Hard to diagnose too, as when things cool down a bit the module may start working again for a while.  

More common, though, is a problem with one or more of the motherboard voltage regulators.  They degrade due to heat over time, and tend to be located close to the CPU where motherboard temps are warmest.  There is usually a visual indication of this kind of failure. Look for leaking or bulging capacitors around the CPU (the capacitors are shaped like little beer cans and usually covered with a vinyl sheath. There should be no signs of leakage (whiteish or brownish goo or perhaps crystalline "feathers") and the sides should be straight and tops should be flat to slightly concave. If the tops or sides look bulged out it is a sign of internal failure that could lead to short circuits and shutdown as above. Also, inspect the MOSFeT devices in the same areas for signs of burning/sparking. Your nose can help...they stink like the seventh level of hell when they burn.  A good light and hand magnifier will help.  

By all means, disconnect the unit from the mains before poking around inside the case.

---

### Post by Adam_GUI on 2018-03-07
Installed and ran psensor.
So, I'm getting temperatures now.
The room stays hot.  So, I guess I'm going to be looking at a 3rd party heat sink.
If it's the room that stays hot and I need to cool the room, or, it's the computer that heats the room, I'm not sure.
Here's the Psensor output.
[ATTACH=CONFIG]278842[/ATTACH]

I don't know if the values are optimal.  I'm not doing anything hardware intensive.
I haven't opened the case again yet to check the hardware, but I remember it being a quad core AMD.
The MOBO had settings for temperature shut-down, but not fan speed that I remember.

---

### Post by QIII on 2018-03-07
Unfortunately, that GUI shows two "temp1" readings and it is impossible to tell which is reading what component.  If you have an AMD processor and that is the one reading 69C, then it is far, far too hot.

Would you please run psensor from the terminal and post the results back here between code tags so we can see the entire output and determine which "temp1" is which?

---

### Post by Adam_GUI on 2018-03-07
> **QIII said:**
> Unfortunately, that GUI shows two "temp1" readings and it is impossible to tell which is reading what component.  If you have an AMD processor and that is the one reading 69C, then it is far, far too hot.

Would you please run psensor from the terminal and post the results back here between code tags so we can see the entire output and determine which "temp1" is which?

Running psensor in term gives me the following output:
 psensor
```
[2018-03-07T22:00:57] [ERR] hddtemp: failed to open connection.
[2018-03-07T22:00:57] [ERR] atasmart: sk_disk_open() failure: /dev/sda.
[2018-03-07T22:00:57] [ERR] atasmart: sk_disk_open() failure: /dev/sdb.
[2018-03-07T22:00:57] [ERR] atasmart: sk_disk_open() failure: /dev/sdc.
```

It also paints this window:
[ATTACH=CONFIG]278843[/ATTACH]
The first Temp1 identifies as lmsensor acpitz-virtual-0 temp1
The second Temp1 identifies as lmsensor k10temp-pci-00c3 temp1

---

### Post by QIII on 2018-03-07
OK, so the second one is your CPU temp.  That temperature, if at idle, is still of great concern because of the way some AMD CPUs report their temperature.

Would you please post the results of 

```
cat /proc/cpuinfo | grep model
```

If your max temp of your CPU is approaching 60C by that reading, you are definitely getting a thermal shutdown unless that is an APU.  60C (per the goofy AMD reading) is the "spontaneously burst into flames and set off fire alarms" limit for most AMD processors -- unless they are APUs with on-die graphics.

---

### Post by Adam_GUI on 2018-03-07
> **QIII said:**
> OK, so the second one is your CPU temp.  That temperature, if at idle, is still of great concern because of the way some AMD CPUs report their temperature.

Would you please post the results of 

```
cat /proc/cpuinfo | grep model
```

If your max temp of your CPU is approaching 60C by that reading, you are definitely getting a thermal shutdown unless that is an APU.  60C (per the goofy AMD reading) is the "spontaneously burst into flames and set off fire alarms" limit for most AMD processors -- unless they are APUs with on-die graphics.

```
cat /proc/cpuinfo | grep model
model		: 1
model name	: AMD FX(tm)-4100 Quad-Core Processor
model		: 1
model name	: AMD FX(tm)-4100 Quad-Core Processor
model		: 1
model name	: AMD FX(tm)-4100 Quad-Core Processor
model		: 1
model name	: AMD FX(tm)-4100 Quad-Core Processor

```

---

### Post by QIII on 2018-03-07
AMD gives the max safe temperature for the FX-4100 as 61C.  You are very close to that at the max, and running at mid-40s at idle is way too hot.  One of my machines has an FX-8350 that idles around 30C and never goes above 50C.  Granted, that is with an after-market cooler.

BUT ... before you rush out and buy an aftermarket cooler, the stock cooler has been shown in many reviews to be perfectly fine under all but the most demanding of circumstances.  Don't spend your money if you don't need to.

Install the lm-sensors package, run sensors-detect and answer "Yes" to all the questions. Reboot.  Now take a look at your fan speeds.  My guess is that the CPU fan will be spinning pretty fast.  If not, your problem may lie there.

Then check that your case is adequately ventilated.  What sort of case do you have?  How many case fans?

If the fan is spinning fast and your case is well ventilated, you may want to check to see that the heat sink is securely mounted.  If it is, disassemble the HSF and check the thermal compound.  If it is dry, replace it.

As awful as that all sounds, don't panic.  Your machine is shutting down to protect itself before damage occurs.  But if this goes on for too long, it will eventually be damaging.

---

### Post by Adam_GUI on 2018-04-11
So, I just now got the heat sink replaced.  I now have a Cooler Master Hyper 212 EVO instead of the stock AMD cooler.
I'm happy to report much more sane numbers.
Before, it was idling at 48-50C.

Now, it's idling at 8-10C.

[ATTACH=CONFIG]279248[/ATTACH]

---

