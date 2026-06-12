---
title: "[hardy] Dell Latitude D420 overheats with new kernel"
date: 2008-05-26
forum: Hardware
---

### Post by ondrass on 2008-05-26
Hello everybody,

my D420 started to heat more (it's not exactly overheating) since I have upgraded to Ubuntu 8.04 LTS.

This seams to be a bug related to kernel, because my two colleagues with Fedora Core have same problem.  Kernel 2.6.22 was ok, 2.6.23 and higher gives us problems.  I'll try some older kernels to isolate this problem and report back.

Anybody with same experience?

Ondrej.

---

### Post by Plexus81 on 2008-06-04
I've got the same problem! The computer seems to be working hard with "nothing" and the fan is running all the time (with no programs running) Fan is speeding up when running 1 program..

Also tryed to set the cpu speed to 800MHz, but the fan is still going.. :(

---

### Post by piginabox on 2008-06-10
i can confirm same problem on my D420.

---

### Post by beefcurry on 2008-06-16
I can also confirm this on my Dell XPS M1330, The heat makes my hands burn, constant crashes etc. Turning of my WLAN moduale reduced the heat from ~70C to 66C which made it abit less crashy if I don't watch videos. I spent most of my time using the Virtual Terminals (Cntrl Alt F1) to do most my work since that keeps temps down to 60C. All the tempretures are recorded with "watch acpi -V" so it should be somewhat accurate.

---

### Post by Plexus81 on 2008-09-06
Got the same problem on my d420. Hardy is working hard with nothing! 

Installed lm-sensors and tuned the CPU down to 800MHz, and the CPU is still hot doing nothing. 

Around 55 C doing nothing.  Running 1 tab in Firefox with flash the CPU goes up to 70 C until the fan goes into hyper mode!

---

### Post by anatolykern on 2009-02-09
I have the same issue with interpid on D420

Windows runs much better in term of the temperature.

I was able to minimize temperature to 52C with i8k, setting cpu to 800MHz and gkrellm running on background (forcing fan to run on highest speed)

[https://bugs.launchpad.net/acpi/+bug/22336](https://bugs.launchpad.net/acpi/+bug/22336)

from my side it looks like a problem with acpi (doesn't using halt instructions and cooling)

$acpi -V
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 51.5 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10
(cooling is always at this state)

$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
polling frequency:       2 seconds
state:                   ok
temperature:             52 C
critical (S5):           107 C
(setting not supported related to cooling_mode)

dmesg:
[    3.100281] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.100382] processor ACPI0007:00: registered as cooling_device0
[    3.100389] ACPI: Processor [CPU0] (supports 8 throttling states)

$ uname -r
2.6.27-11-generic

---

### Post by mr_manny on 2010-02-03
new adopter to 10.04 on my D420...everything works out of the box :)

temp doesn't seem to bad, although I noticed temp readings match yours: 

$ acpi -V
Battery 0: Charging, 27%, 00:57:46 until charged
Battery 0: design capacity 3800 mAh, last full capacity 3977 mAh = 100%
Adapter 0: on-line
Thermal 0: ok, 54.5 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 107.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10

$ uname -a
Linux d420 2.6.32-12-generic #16-Ubuntu SMP Wed Jan 27 18:34:19 UTC 2010 i686 GNU/Linux

---

### Post by Berniebln on 2010-02-06
Also have this problem on an Asus Notebook with a AMD Turion X2 Dual-Core Mobile RM-70 (it is 64 bit, but I have 32 bit Ubuntu 9.10 installed).

If I start-up, and the system is idle, and although the fan is running on full speed all the time, temperature can rise up to 95°C. If I start any programs, it's getting worse. 

Right now I've installed the Gnome CPU applet which allows me to manually switch the two cores to "powersafe mode", which keeps the CPU temperature (ACPI/THRM) around 80°.

I did not have this problem in 9.4, and I think it's just "lately" (since a month or so). In windows, it never happens, the system stays cool and the fan usually runs on a low speed.

Bernhard

---

