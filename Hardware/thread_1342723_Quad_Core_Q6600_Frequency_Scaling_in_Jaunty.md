---
title: "Quad Core Q6600 Frequency Scaling in Jaunty"
date: 2009-12-01
forum: Hardware
---

### Post by SabreWolfy on 2009-12-01
[B][COLOR="Red"][SIZE="5"]UPDATE: SOLVED:[/SIZE]
My bad. The BIOS needed to be updated to include the "EIST" functionality to enable Intel SpeedStep.[/COLOR][/B]

I'm running Jaunty Desktop 32bit (fully updated) on an Intel Quad Core Q6600 with a Gigabyte GA-EG31M-S2 motherboard.

When I add the CPU Frequency Scaling applet to my GNOME panel, a dialog appears with a sad story:

```

CPU frequency scaling unsupported

You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

```

I've already done:

```

sudo dpkg-reconfigure gnome-applets

```

and selected "Yes".

"powernowd" is selected under System --> Administration --> Services.

I've installed "cpufrequtils" and "cpufreqd".

"cpufreq-info" tells me:

```

cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 3:

```

"cpufreq-selector" tells me "No cpufreq support".

Output from "/proc/cpuinfo" reports that all four cores are cruising at 2.4GHz, which seems very wasteful.

Any ideas on "enabling" CPU Frequence Scaling / SpeedStep on this machine? How do I get the various tools to even recognize the processor correctly?

I've checked for BIOS updates; some are available, but they address unrelated issues, so I have not flashed the machine's BIOS.

[I have a Q8200 running 32-bit Karmic Server and the various tools above recognize the processor and work correctly. That CPU can only step between 2.0GHz and 2.3GHz, but at least all four cores there are sitting at 2.0GHz when not loaded.]

**Edit:** Despite "powernowd" being selected as mentioned above, it was in fact not installed. I installed it (which removed cpufreqd). However, during the installation, powernowd reported the following:

```

 * Starting powernowd...
 * CPU frequency scaling not supported...

```

Running "powernowd -d -v -v" gives me more information:

```

PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
...
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
...

```

The first two points are fine I'm sure.
No idea about the last two points ... ?

---

### Post by JBAlaska on 2009-12-01
Check the output of this:
```
sudo -s
echo 2800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
```

---

### Post by SabreWolfy on 2009-12-01
> **JBAlaska said:**
> Check the output of this:
```
sudo -s
echo 2800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
```

That's the problem -- my directory tree does not have a "cpufreq" folder under each of the "cpu?" folders ... !

**[COLOR="Red"]Solved: BIOS update was required.[/COLOR]**

---

### Post by SabreWolfy on 2009-12-01
It seems that the Q6600 does not support CPU frequency scaling. The Intel website suggests that it does (SpeedStep). However, there is no setting to enable it (EIST) in my BIOS. The BIOS manual reports that the setting is present only if a compatible CPU is present, so I must therefore assume that the Q6600 which I have is not compatible.

**[COLOR="Red"]Solved: BIOS update was required.[/COLOR]**

---

