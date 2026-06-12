---
title: "lm-sensors with Core II. Do they really run this cool?"
date: 2008-08-26
forum: General Help
---

### Post by mrmorris on 2008-08-26
I wonder if the values from lm-sensors are accurate on my system. I've attached a screenshot with the ouput of "sensors" command as well as how the gnome panel renders these. Notice how my 2 cores (it's a Core II 6750) are around 24c and 21c. 

That seems remarkable low and not at all consistent with what readings I would get from Windows. The room I am sitting in happens to be 26c, the system itself 43c and the CPU temperature (motherboard sensor?) 38c?

[IMG]http://82.103.135.236/dump.png[/IMG]

I'd appreciate some feedback from other people running lm-sensors and with a Core II. I don't understand the numbers I am seeing.

Thanks,
Casper

---

### Post by Sycron on 2008-08-26
It's also important what cooling system do you have... WOW 75C at GPU ?

---

### Post by MJWitter on 2008-08-26
Hi,

I am running a core II Quad and the CPU usually runs around 50c in linux(no idea if thats correct either, but similar in windows). System Temp is 38. All air cooling..
So yours could be correct, although I think the individual core readings are on the low side..

---

### Post by mrmorris on 2008-08-26
System is optimized for silence, meaning I have a large but common Zalman copper cooler and a slow moving (1100rpm) fan on top of it. It's slightly underclocked (2.5GHz rather than 2.66GHz) and power scheme is on-demand (2GHz).

The GPU is running a bit warm yeah, a GeForce 8600 GTS/256MB/720MHz. Looking into how to underclock it, hardly needed for Compiz (but nice for the occasional gaming).

Thanks guys for the feedback.
/Casper

---

