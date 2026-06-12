---
title: "Dell Optiplex 780 system fan keeps running on high"
date: 2018-01-02
forum: Hardware
---

### Post by itbedguy on 2018-01-02
I installed Ubuntu server 16.04.3 on an old Dell Optiplex from 2011 with an Intel Core 2 Duo E7500 @2.93Ghz, 2 cores. I’m using it as a Plex server. Plex runs pretty well considering how dated this machine is. The only issue is that the system fans run high speed all the time, regardless if the CPU is being taxed or not. I suspect it is some sort of ACPI compatibility issue. I’m somewhat a newbie when it comes to Linux. Are there any Dell specific drivers I could try to fix the problem?  Any help is greatly appreciated.

---

### Post by DuckHook on 2018-01-02
Welcome to the forums, itbedguy.

The combination of *lm-sensors* and *fancontrol* may work for you:```
sudo apt update && sudo apt install lm-sensors fancontrol
```
Instructions on setting up/using *lm-sensors*: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
Instructions for setting up *fancontrol* are further down the same page: [https://help.ubuntu.com/community/SensorInstallHowto#Controlling_fanspeeds_according_to_sensor_values](https://help.ubuntu.com/community/SensorInstallHowto#Controlling_fanspeeds_according_to_sensor_values)

Note that *fancontrol* may not work on your machine, and *lm-sensors* is not always easy to set up. If you are lucky, your exact MOBO and chipset will be recognized with proper values already populated. Sometimes, you need to create a config file for your mobo/CPU/GPU/chipets. In the worst case, your MOBO is not recognized. But—such caveats aside—once set up properly, it is pretty much boot and forget.

---

### Post by gordintoronto on 2018-01-03
Any chance the CPU heat sink is clogged up, or the fan has stopped working? I just went through this with my desktop.

---

### Post by QIII on 2018-01-03
If you don't have any monitoring set up, reboot and immediately enter your BIOS setup to see if there is a temp indicator.  Let us know what you find.

---

### Post by itbedguy on 2018-01-05
Thanks everyone for the information.  Turns out upon closer examination that a bad noisy fan in the power supply is the culprit.  My apologies for not noticing that before, but, at least I learned a few things in the process.

---

### Post by sccman on 2018-01-05
No problem :D

I'm not sure if you're doing it but just a friendly safety warning: DO NOT OPEN THE POWER SUPPLY UNDER ANY CIRCUMSTANCES. They have electricity that runs through them even after you unplug it from the wall and computer. Touching the wrong wire can actually kill you from the electricity. We'd rather you be alive than dead.

---

### Post by DuckHook on 2018-01-05
> **itbedguy said:**
> &#8230;a bad noisy fan in the power supply is the culprit&#8230;

> **sccman said:**
> &#8230;DO NOT OPEN THE POWER SUPPLY UNDER ANY CIRCUMSTANCES. They have electricity that runs through them even after you unplug it from the wall and computer. Touching the wrong wire can actually kill you from the electricity. We'd rather you be alive than dead.
&#8593;+1

A new PSU is a cheap fix. You might even be able to salvage an old PSU from some computer shop for next to nothing.

Please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

Good Luck and Happy Ubuntuing!

---

