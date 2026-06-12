---
title: "emifreq"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by smtanner on 2005-03-26
Nice cpu throttle controller.  

[http://zzrough.free.fr/emifreq.php](http://zzrough.free.fr/emifreq.php)

Version 0.18 would be a nice addition to the ubuntu desktop.  Has profiles like "performance" "Power Saving" and "automatic".

---

### Post by kperkins on 2005-03-28
Try emifreq-applet.  It's in the repositories. (Although it's version 1.7--is there a big diff?)

---

### Post by wildcard on 2005-05-11
0.18 has support for the ondemand scaling governor.

I think this is important since the only way I could get my CPU to not be running at 100% performance all the time was to go with cpufreqd rather than powernowd. I did some editing of the cpufreq.conf to enable the kind  of scaling I wanted and also added the ondemand and powersave governors to a startup script.

I'd rather run just one applet to monitor CPU speed and temp (the 0.18 EMI applet) rather than two (Ubuntu's default frequency scaling monitor + the 0.17 EMI applet).

---

### Post by CameronCalver on 2006-05-21
where is cpufreq.conf

---

