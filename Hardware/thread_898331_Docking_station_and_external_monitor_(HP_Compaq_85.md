---
title: "Docking station and external monitor (HP Compaq 8510w)"
date: 2008-08-23
forum: Hardware
---

### Post by mandragor on 2008-08-23
Hi guys!

I'm running Kubuntu 8.04 and KDE 4.1 on a Compaq 8510w, often used in a
HP Docking-station with a HP w2408 24" monitor that supports 1920x1200,
while the laptop's monitor only supports 1680x1050. 

Using nvidia-settings I can set the external monitor to clone the laptop-
monitor, but then I have to set the resolution to 1680x1050 on both. What
I want is for X/KDE to automagically change the settings (like nvidia-
settings does) on-the-fly when I open or close the lid. With the lid
closed I'd like to use just the external monitor with a resolution of
1920x1200 and with the lid open I'd prefer to use just the internal-
monitor in 1680x1050.

So far I've found this tutorial by Xthor that provides a script to setup
the monitors during boot by checking /proc/acpi/button/lid/*/state
[http://www.xthorsworld.com/?p=20](http://www.xthorsworld.com/?p=20)
I would prefer to not have to reboot several times each day, for several 
reasons, but wasting time and it being very windowsy-behaviour are two.:)

What methods are available to check if /proc/acpi/button/lid/*/state
has changed and execute a script depending on what the new state is?

Thanks in advance

---

