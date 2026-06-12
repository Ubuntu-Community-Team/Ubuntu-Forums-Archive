---
title: "temp monitor"
date: 2010-05-29
forum: Hardware
---

### Post by narasimhan1990 on 2010-05-29
suggest a good temp monitor software.
i tried lm-sensors but it shows only one temperature(i did use sensor detect and yes to all questions and added the lines to the file).

my mobo: biostar ta790gxb
proc: amd phenon II x4 940be
gpu: power color HD 4870

---

### Post by jerrrys on 2010-05-29
i like computertemp myself, but heres others that are in synaptic package manager

[ATTACH]158660[/ATTACH]

---

### Post by IcarusR on 2010-05-29
If lm-sensors does not detect any sensors then I would think that you are going to struggle to get anything to work.

computertemp will not display anything if lm-sensors can not detect sensors.

---

### Post by narasimhan1990 on 2010-05-31
i guess all gui's are based on lm-sensors. 
any user having biostar mobo can shed some light?

---

### Post by bra|10n on 2010-05-31
post your output of *sensors* in a terminal pls

---

### Post by narasimhan1990 on 2010-05-31
here's the output u asked for
> acpitz-virtual-0
Adapter: Virtual device
temp1:       +31.0°C  (crit = +75.0°C) 

---

### Post by dino99 on 2010-05-31
[http://www.lm-sensors.org/wiki](http://www.lm-sensors.org/wiki)

you need fancontrol and set /etc/fancontrol

[http://www.google.com/search?client=ubuntu&channel=fs&q=acpitz-virtual-0%2Bfancontrol&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=acpitz-virtual-0%2Bfancontrol&ie=utf-8&oe=utf-8)

---

