---
title: "coretemp Using undocume
nted features, absolute temperature might be wrong!"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by mitsuho on 2007-11-19
7.10 kernel2.6.22-14 on C2D E6850 & G33 & ICH9R coretemp put

    too low temperature(12C and 15C)

and the warning in kern.log as 'coretemp coretemp.0: Using undocume
nted features, absolute temperature might be wrong!'

I think these temperature is doubtful. Does someone know the solution ?

I have read the coretemp source code, at this moment I don't find any wrong code.
I know there have been some patch about Intel's Undocumented features, and 7.10
hwmon/coretemp might seem to be reflected already.

---

### Post by Huzudra on 2008-01-19
I'm having a similar issue with a Foxconn board (965GZ chipset) and an Intel E2140 clocked at 2.13Ghz.  I installed the lm-sensors and the applet for temperature monitor on the bar and i'm seeing a 10C (50F) idle...which is pretty much impossible since its atleast 60F in this room.  now i know the senor readings do change, under load the temperature rises.  using cpuburn with burnP6 (2 instances running) I was able to raise the temp to about 35-40C which sounds more reasonable but since the idle is soo low i'm not sure if thats the true high temp.  i knew this was a cool running cpu but not this cold blooded!:confused:

---

