---
title: "Slow Processor Clock"
date: 2009-08-02
forum: Hardware
---

### Post by julian.irwin on 2009-08-02
I have a Intel E7500 @2.93ghz processor in a computer that I just built. It is only clocking in at 2.2Ghz. Whats wrong? Im not overclocking it at all. Should I just crank up the DOC in the BIOS until my processor clocks where it is supposed to. Is DOC bad if I use it all the time?

On the side, is there a linux utility or shell command I can use to get info on my processor?
Thanks!

---

### Post by hw-tph on 2009-08-03
Your CPU is not running at maximum speed at all times to preserve energy and to prevent your computer's fans to run at full speed. The default Ubuntu installation comes with CPU frequency enabled in order to achieve this.

To see information about your CPU, type **cpufreq-info** at the command line. There is an applet that you can add to the bar at the top of the screen to either control speed manually or to set different frequency scaling governors.

---

