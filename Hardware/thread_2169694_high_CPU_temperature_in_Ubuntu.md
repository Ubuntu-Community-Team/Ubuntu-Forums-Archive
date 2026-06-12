---
title: "high CPU temperature in Ubuntu"
date: 2013-08-23
forum: Hardware
---

### Post by Ladybirdie on 2013-08-23
Hi All!


I have a PC with C2D E6600 with stock fan and no  overclocking. Two weeks ago I did a reinstall of Ubuntu 10.04, 12.04.2  (latest - gnome) and Win XP side by side because of a new hdd. BIOS is the  latest for the Intel dg965wh mobo. Because of the high temp described  below I've reapplied thermal paste a week ago and cleaned the fan, no change.
    
In XP the idle temperature is around 35-40C (HWinfo and  coretemp), while in Ubuntu (both) it's around 50C. In Ubuntu even  opening a new tab in Firefox causes the coretemp to spike to 60C then as long as the Firefox is open it's around 55-62C. Doing the  same in XP results temperatures around 40-42C. Room ambient  temperature is around 25C, two basic 8cm intake and out-take fans (around  1600-1800RPM) are installed in a regular case.

Speedstep  in BIOS is enabled, in Ubuntu I use indicator-cpufreq. For some reason  the indicator shows only two frequencies, 2.4GHz and 1.6GHz but I can't switch to 1.6GHz. Coretemp in  XP shows frequency 1.9-2GHz when idle, 2.3-2.4 under load, and no other  frequencies. In XP with HWinfo I could check the case fan speeds, but in Ubuntu  lm-sensors/sensors-detect cannot find the fans so no checking there, but  they seem to be spinning and since both are 3 pin fans they should be at max.  speed all the time. In BIOS aggressive cooling is set.

   
What can cause the 10-15C temperature difference? How to lower the temp in Ubuntu?

On the  previous hdd/system (XP - 10.04 wubi, for 3 years) I also had this  temperature difference when idle, but now it's really bugging me,  because just browsing never resulted 60C before, just around 52C. My concern is  that in Ubuntu where I usually work, using one core for calculations  raises the temp to 71C, and if I use both, then it's flares up to 81-82C which is not  good since 85C is the maximum for E6600. In XP I don't remember seeing  temperatures above 55C. 


Thanks in advance!

---

