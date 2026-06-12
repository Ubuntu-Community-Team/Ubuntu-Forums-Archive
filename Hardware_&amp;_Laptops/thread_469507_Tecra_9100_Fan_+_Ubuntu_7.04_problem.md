---
title: "Tecra 9100 Fan + Ubuntu 7.04 problem"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by sirbrown on 2007-06-10
Hello,

I am hoping someone here might be able to help me with a problem
I have been having with using Ubuntu (currently 7.04) with my Toshiba
Tecra 9100.  Everything is working very well, except for the CPU fan,
which will not shut off once activated.  

I have tried to do a couple things about this.  First I went
to /proc/acpi/thermal_zone/THRM/ and checked to see whether the
temperature was in fact overheated by running "cat temperature
trip_points", resulting in the following:

temperature:             50 C
critical (S5):           99 C
passive:                 98 C: tc1=9 tc2=2 tsp=1800 devices=0xdeaf82e8 
active[0]:               98 C: devices=0xdeb05748 
active[1]:               98 C: devices=0xdeb05748 

This suggests to me that the temperature is nowhere near the threshold
for active cooling.  So, I guess that maybe I should turn the fan off
manually.  I installed both the "toshutils" package by Jonathan Buzzard
as well as the "toshset" package, yet neither of them permit me to turn
off the fan in the usual way.  The only solution that has worked thus
far is to toggle the cooling mode using toshset from "quiet" to
"perform" and back again.

I also tried following the suggestion on an Ubuntu page that I install
lm-sensors and sensors-detect, but it didn't find any sensors on my
machine, and hence isn't useful.

Has anyone else observed this problem with the Tecra 9100 or another
Toshiba laptop?  If so, have you found a way around it?  Your advice
would be tremendously appreciated!

Thank you,
Colby

---

### Post by LazyTownRocks on 2007-07-02
something similaer here ==> [http://ubuntuforums.org/showthread.php?t=471868&highlight=tecra](http://ubuntuforums.org/showthread.php?t=471868&highlight=tecra)

---

