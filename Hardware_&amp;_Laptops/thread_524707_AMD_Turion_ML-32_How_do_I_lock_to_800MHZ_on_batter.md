---
title: "AMD Turion ML-32: How do I lock to 800MHZ on battery?"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by mikeypizano on 2007-08-13
:mad: How to I lock the CPU instead of it just scaling?

---

### Post by Bachstelze on 2007-08-13
As I told you, using cpufreq :

```
sudo apt-get install cpufrequtils
```

then do a *cpufreq-info* and paste what you get.

---

### Post by mikeypizano on 2007-08-13
Here is the output:
```
mikeypizano@mikeypizano-acer:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 800 MHz and 1.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

---

### Post by Bachstelze on 2007-08-13
"current CPU frequency is 800 MHz."

You're there. Try to do some CPU-intensive work and see if the frequency gets higher. IF it does, do a

```
sudo cpufreq-set -g powersave
```

to lock it to the lowest possible speed.

---

### Post by mikeypizano on 2007-08-13
Problem ;)
```

mikeypizano@mikeypizano-acer:~$ sudo cpufrq-set -g powersave
sudo: cpufrq-set: command not found
mikeypizano@mikeypizano-acer:~$ 

```

---

### Post by Bachstelze on 2007-08-13
Typo ;)

---

### Post by mikeypizano on 2007-08-13
Woo it works!

---

### Post by syko21 on 2007-08-13
If you want to add battery life and not just reduce power consumption I suggest laptop-mode as it changes the way data is written to the hard drive to reduce power usage.
```
sudo apt-get install laptop-mode laptop-mode-tools laptop-detect cpufreqd cpufrequtils
sudo gedit /etc/default/acpi-support

```at the very end there is an option "ENABLE_LAPTOP_MODE=false", set that to true and thats it.
Laptop-mode also has a very useful configuration file that has cpu frequency settings and a lot of other options to save power.
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```

---

### Post by mikeypizano on 2007-08-14
=D>=D>Thanks!=D>=D>

Question: should I restart X as my CPU is stuck at full speed even though I changed it?

---

### Post by syko21 on 2007-08-14
Restarting X is just for display configurations and input devices. You should reboot instead.

---

### Post by mikeypizano on 2007-08-14
After the reboot, it says my CPU doesn't support scaling which worked fine before...

---

### Post by Bachstelze on 2007-08-14
Try to load your cpufreq driver manually :

```
sudo modprobe powernow-k8
```

---

### Post by mikeypizano on 2007-08-14
Okay, I can do by hand only. The menu on the scaler doesnt show up.

---

### Post by syko21 on 2007-08-14
follow the instructions found here
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)
to get your scaling working again.
Then edit your /etc/laptop-mode/laptop-mode.conf
```

...
###############################################################################
# CPU frequency scaling and throttling
# ------------------------------------
#
# Laptop mode tools can automatically adjust your kernel CPU frequency
# settings. This includes upper and lower limits and scaling governors.
# There is also support for CPU throttling, on systems that don't support
# frequency scaling.
#
# This feature only works on 2.6 kernels.
###############################################################################

# Should laptop mode tools control the maximum CPU frequency?
CONTROL_CPU_FREQUENCY=1 

# Legal values are "slowest" for the slowest speed that your
# CPU is able to operate at, "fastest" for the fastest speed,
# "medium" for some value in the middle, or any value listed in
# /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies.
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersave
..........

# Should laptop mode tools control the CPU throttling? This is only useful
# on processors that don't have frequency scaling.
# (Only works when you have /proc/acpi/processor/CPU*/throttling.)
CONTROL_CPU_THROTTLING=0

# Legal values are "maximum" for the maximum (slowest) throttling level,
# "minimum" for minimum (fastest) throttling level, "medium" for a value
# somewhere in the middle (this is usually 50% for P4s), or any value listed
# in /proc/acpi/processor/CPU*/throttling. Be careful when using "maximum":
# this may be _very_ slow (in fact, with P4s it slows down the processor
# by a factor 8).
BATT_CPU_THROTTLING=medium
LM_AC_CPU_THROTTLING=medium
NOLM_AC_CPU_THROTTLING=minimum



...

```

---

### Post by mikeypizano on 2007-08-14
heres mine:
```

###############################################################################
# CPU frequency scaling and throttling
# ------------------------------------
#
# Laptop mode tools can automatically adjust your kernel CPU frequency
# settings. This includes upper and lower limits and scaling governors.
# There is also support for CPU throttling, on systems that don't support
# frequency scaling.
#
# This feature only works on 2.6 kernels.
###############################################################################

# Should laptop mode tools control the maximum CPU frequency?
CONTROL_CPU_FREQUENCY=0

# Legal values are "slowest" for the slowest speed that your
# CPU is able to operate at, "fastest" for the fastest speed,
# "medium" for some value in the middle, or any value listed in
# /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies.
BATT_CPU_MAXFREQ=medium
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=ondemand
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=performance

# Should laptop mode tools control the CPU throttling? This is only useful
# on processors that don't have frequency scaling.
# (Only works when you have /proc/acpi/processor/CPU*/throttling.)
CONTROL_CPU_THROTTLING=0

# Legal values are "maximum" for the maximum (slowest) throttling level,
# "minimum" for minimum (fastest) throttling level, "medium" for a value
# somewhere in the middle (this is usually 50% for P4s), or any value listed
# in /proc/acpi/processor/CPU*/throttling. Be careful when using "maximum":
# this may be _very_ slow (in fact, with P4s it slows down the processor
# by a factor 8).
BATT_CPU_THROTTLING=medium
LM_AC_CPU_THROTTLING=medium
NOLM_AC_CPU_THROTTLING=minimum

```

---

### Post by syko21 on 2007-08-14
```

###############################################################################
# CPU frequency scaling and throttling
# ------------------------------------
#
# Laptop mode tools can automatically adjust your kernel CPU frequency
# settings. This includes upper and lower limits and scaling governors.
# There is also support for CPU throttling, on systems that don't support
# frequency scaling.
#
# This feature only works on 2.6 kernels.
###############################################################################

# Should laptop mode tools control the maximum CPU frequency?
CONTROL_CPU_FREQUENCY=1

# Legal values are "slowest" for the slowest speed that your
# CPU is able to operate at, "fastest" for the fastest speed,
# "medium" for some value in the middle, or any value listed in
# /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies.
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersave
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=performance

# Should laptop mode tools control the CPU throttling? This is only useful
# on processors that don't have frequency scaling.
# (Only works when you have /proc/acpi/processor/CPU*/throttling.)
CONTROL_CPU_THROTTLING=0

# Legal values are "maximum" for the maximum (slowest) throttling level,
# "minimum" for minimum (fastest) throttling level, "medium" for a value
# somewhere in the middle (this is usually 50% for P4s), or any value listed
# in /proc/acpi/processor/CPU*/throttling. Be careful when using "maximum":
# this may be _very_ slow (in fact, with P4s it slows down the processor
# by a factor 8).
BATT_CPU_THROTTLING=medium
LM_AC_CPU_THROTTLING=medium
NOLM_AC_CPU_THROTTLING=minimum


```

---

### Post by mikeypizano on 2007-08-14
Thanks eveyrthing works fine!

---

