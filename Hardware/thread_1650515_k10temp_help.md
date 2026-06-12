---
title: "k10temp help"
date: 2010-12-21
forum: Hardware
---

### Post by z3uSS on 2010-12-21
hy ppl, need some help with sensors for temp applet

output of uname -a 

"Linux HP 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux"

so i have an HP pavilion and really need to monitor my proc temp. with this in mind i've installed lm_sensors ... got stuck with k10temp installing ... got trough that .. but still i have no output for sensors. when i go sensors-detect it's ok ... k10temp is there ... but it seems it's not working ... pls some help here ?

also output for 
$ sudo lsmod | grep "k10temp"
k10temp                 1676  0

---

### Post by Fir3chi3f on 2010-12-22
What applet are you trying to use? I think k10 is for AMD, is that the CPU you have?

---

### Post by z3uSS on 2010-12-22
yep i have an amd athlon x2, the applet is "Hardware monitoring tool". but the problem is not with the applet ... even sensors can't read the temp.... even if the driver it is installed

---

### Post by Fafler on 2010-12-22
Google the specific laptop model + sensors linux and see if anyone has similar problems.

---

### Post by z3uSS on 2010-12-22
did that ... the problem is that did't manage to find an answer to that isue. and really need that sensor cause i have an hardware problem and need to find if it's the proc or the cooler responsable for some instant hibernation ( unasked ones )

---

