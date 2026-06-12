---
title: "Computer Temperature Monitor applet"
date: 2009-09-18
forum: Hardware
---

### Post by a__l__a__n on 2009-09-18
I have installed the Computer Temperature Monitor applet in Ubuntu 9.04 (64 bit) on my HP nc8430 laptop.  It seems to be working to an extent.. but the alarms are not correct.  Under preferences, I set the alarm limit to 60 degrees as a test (working in Celsius) and set it to alarm when the temp is higher than limit.  The current TZ0 temp was 50.  I then ran super_pi in a loop to heat things up, and it went up over 60 without triggering an alarm. (I set the alarm command to zenity --info --text=TZ0  

I turned on logging, and it is logging alarms on TZ0 when the temp is below the limit.

Any idea what is wrong?

---

