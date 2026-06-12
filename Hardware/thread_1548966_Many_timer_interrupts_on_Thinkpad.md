---
title: "Many timer interrupts on Thinkpad"
date: 2010-08-09
forum: Hardware
---

### Post by yankee83 on 2010-08-09
Hi,

a powertop output on my Lenovo T400 looks like this:
```
Your CPU supports the following C-states : C1 C2 C3 C4 C5 C6 
Your BIOS reports the following C-states : C1 C2 C4 
Cn                Avg residency
C0 (cpu running)        ( 2.8%)
polling           7.7ms (97.2%)
C1 mwait          0.0ms ( 0.0%)
C2 mwait          0.0ms ( 0.0%)
C4 mwait          0.0ms ( 0.0%)
P-states (frequencies)
Turbo Mode     1.7%
  2.54 Ghz     0.2%
  1.60 Ghz     0.0%
   800 Mhz    98.1%
Disk accesses:
The application 'flush-252:0' is writing to file '.xsession-errors' on /dev/dm-0
Wakeups-from-idle per second : 126.6    interval: 15.0s
no ACPI power usage estimate available
Top causes for wakeups:
  31.5% ( 94.3)   [extra timer interrupt]
  27.8% ( 83.5)   plugin-containe
  18.1% ( 54.3)   [iwlagn] <interrupt>
  15.8% ( 47.3)   firefox-bin
  ....

An audio device is active 100.0% of the time:
hwC0D1 Conexant ID 2c06 

A USB device is active 100.0% of the time:
USB device  1-6 : Integrated Camera (Chicony Electronics Co., Ltd.)

```

Somehow the CPU spends most of its time in the polling state and does not turn to any lower level. I believe that this is caused by the numerous extra timer interrupts preventing the CPU from changing to another C-state. If I add nolapic to the boot options, the problem is solved, there are no extra timer interrupts and the CPU spends most of its time in C4 when idle. However, adding nolapic causes the system to become a bit unreactive to inputs (e.g. trackpad).

I have hpet=force on the boot options and hpet is the current clocksource. Available clock sources are: hpet acpi_pm jiffies tsc.

```

grep Device /proc/timer_list

Tick Device: mode:     0
Clock Event Device: hpet
Tick Device: mode:     0
Clock Event Device: lapic
Tick Device: mode:     0
Clock Event Device: lapic

```

Do you have any idea how I can get rid of the timer interrupts? Maybe someone can also tell me how to permanently put the webcam and the audio card into suspend.

Thank you very much.

---

### Post by yankee83 on 2010-08-11
No idea? :(

---

### Post by PresenceofMind on 2010-08-11
Write your own modules into the Linux kernel.....

---

### Post by yankee83 on 2010-08-11
Any less time-consuming suggestion? :P

---

### Post by yankee83 on 2011-09-26
I actually still have this problem. Are there any new insights maybe? :)

---

