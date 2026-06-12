---
title: "Ubuntu breaks Battery in 11.04?"
date: 2011-08-18
forum: Hardware
---

### Post by dohomi on 2011-08-18
Hello,

I'm using Ubuntu now for around 3 months on my Lenovo T410 and realized that the battery life become unbelievable bad. It even doesn't reach 1 hour (on Win7 around 2). I looked up 
cat /proc/acpi/battery/BAT*/info
> 
present:                 yes
design capacity:         5616 mAh
last full capacity:      2609 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 130 mAh
design capacity low:     18 mAh
cycle count:		  0
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            42T4791
serial number:           13684
battery type:            LION
OEM info:                SANYO


Before I started with Ubuntu my battery life showed 95% of its capacity, now it seems that it only has the half.

What could get wrong with the battery management, it seems that Ubuntu really damages the battery of my Laptop...

Appreciate any help!
domi

---

### Post by IWantFroyo on 2011-08-18
You might want to go into your BIOS and clear your battery stats.

I've never done this on a computer (never had the need to), but it does wonders when switching Android ROMS.

---

### Post by dohomi on 2011-08-18
Hey, many thanks for your hint, but how do I clear the BIOS stats?

---

### Post by IWantFroyo on 2011-08-18
Almost everyone's BIOS is different. I'll edit my post to give my lappy's solution in a minute.

Mainly you just have to look around.

EDIT- I couldn't find anything. I've heard of clearing your battery stats on a computer before. Does anyone else know? I'd be interested in hearing how to do it, too.

---

### Post by dohomi on 2011-08-18
There is an open bug report on this issue, I hope it gets solved soon, because the report is from 2008. My laptop is actually totally useless on battery power, with less than 1 hour battery life...I hope my hardware didn't break though

---

### Post by Alastair Rae on 2011-09-14
> **dohomi said:**
> There is an open bug report on this issue, I hope it gets solved soon, because the report is from 2008. My laptop is actually totally useless on battery power, with less than 1 hour battery life...I hope my hardware didn't break though
There doesn't seem to be any progress on this. Looks like it's back to windows for me. (edit) I'm not that desperate - I've downgraded to 10.04 to see if that improves battery life.

---

### Post by dohomi on 2011-09-14
Hi,

I you like your battery, better do this. In 3 months of use I reduced the capacity of my battery from 85% to 35%...Not good...If I reboot my system with windows it says I need to buy a new one.

---

### Post by diasf on 2011-09-14
There's 2 issues on this problem

1) Newer kernels (2.6+?) use 30% more power than before. That's just like that, AFAIK won't change soon
2) You battery seems "uncalibrated" for me. The battery reports as full, but is on 50% capacity or so. Google ftw on ways to recalibrate it (I can remember, but usually involves using it all, charging for X hours and so)

---

### Post by dohomi on 2011-09-14
Hi,

I am using TLP for the battery life, but still after calibrating not much difference. But I gonna keep using it, to many ++ for Ubuntu. Hopfully the battery problem gets solved in newer versions.

---

