---
title: "Laptop HOT Ubuntu Lucid Lynx"
date: 2010-05-11
forum: Hardware
---

### Post by mearsy94 on 2010-05-11
Hi, I've recently installed Ubuntu Lucid Lynx 10.04 LTS on my Compaq Presario 300-EV.
It all works fine, The drivers etc, But the problem is, That it's getting so darn hot - I've cleaned out the fans and everything but even as idle, It continues to overheat. I dualboot with Windows XP and Using XP keeps it as cool as a cucumber, So is there any way i can cool down my laptop inside Ubuntu without making hardware modifications?
Thanks in advanced.

---

### Post by Garcon on 2010-06-22
I have the same problem with an Acer Aspire 8530. This laptop is very silent and cool while on win7, on ubuntu the fans (recently cleaned) go crazy and temp averages 55-60 degrees.

Any tips?

---

### Post by FactTech on 2010-06-22
You should both check to see if CPU frequency scaling is working properly. If it is not, the CPU is probably running full-speed all the time, resulting in overheating.

Right-click on an empty part of the status bar at the top of your screen and add the CPU Frequency Scaling applet. It may help.

---

### Post by kleeman on 2010-06-22
Might be this:

[http://ubuntuforums.org/showpost.php?p=9388766&postcount=31](http://ubuntuforums.org/showpost.php?p=9388766&postcount=31)

---

### Post by Garcon on 2010-06-23
Hm, in my case powertop shows other problem:

[Rescheduling interrupts] <kernel IPI> uses ~ 50% of wakeups. Will have to look deeper into this. Thanks for the suggestion.
Next in top are:
10.7% ( 99.4)   pulseaudio
10.2% ( 94.0)   [kernel scheduler] Load balancing tick

---

### Post by anantshri on 2010-06-23
few tips.

if you are having ATI or NVIDIA graphics card install the official driver and not the opensource one.

secondly load balancing tick is something we can't do much except at places it is stated that shifting to karmic kernel can help but that is not yet tested.

I was having 55-60 degree temp with opensource ATI. but with official driver temp is now in range of 45-50.

---

### Post by Garcon on 2010-06-23
Thanks.
I was using open source graphic drivers as well, but I switched already (bye bye vgaswitcheroo :( ). Their quality is still very poor.
I'm not going to use the older kernel yet.

---

