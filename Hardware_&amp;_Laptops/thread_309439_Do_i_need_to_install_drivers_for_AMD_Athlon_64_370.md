---
title: "Do i need to install drivers for AMD Athlon 64 3700+???"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by abh83 on 2006-11-29
Hello,

I'm new to ubuntu (and Linux in general). I have an acer aspire 1520 (1525WLMi).

Ubuntu seems to be running fine and i've set it up just the way i like it.

However, in windows xp my fan is a lot quieter and in ubuntu its loud. I'm monitoring my cpu frequency and its at 800MHz most of the time which is good and normal.

Therefore i was wondering if (maybe) i need to install drivers for my AMD Athlon 64 3700+???

thx in advance
abh83

---

### Post by KingBahamut on 2006-11-29
Drivers arent nessecary. You might want to look into powersave or powernow installation 

sudo apt-get install powernowd 

It provides battery, temperature, ac, cpufreq (SpeedStep, Powernow!) control and monitoring.

---

### Post by abh83 on 2006-11-29
thx but i already have that installed is there anything else i could try?

> Reading package lists... Done
Building dependency tree... Done
powernowd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Streborekul on 2006-12-06
Hi,

I too was looking at this. I have powernowd installed, but simply can't find where/how to control CPU performance of my AMD XP 64 x2 4200+. I see in my system monitor it is running at 1 GHz (max speed should be 2.2GHz).

Anybody?

---

### Post by Paul_Whelan on 2006-12-11
Hi,

I have the powernowd running and it works automatically, i.e. when my system is not doing much it scales my cpu back to 1Ghz, and when it needs it, it scales it up to 2.4Ghz, or whatever it is (my cpu is a AMD64 3700+) If you install the frequency scaling applet it should reflect the current status (that's for Ubuntu, for those using Kubuntu or Xubuntu I'm afraid I can't help)

Hope this is of help.

---

