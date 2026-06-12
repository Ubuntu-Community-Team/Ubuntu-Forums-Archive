---
title: "Anyway to manually control the CPU speed on a centrino?"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by taseal on 2005-12-21
I have a centrino based laptop (asus A3500N) and the laptop will last a while on lowest 600mhz setting, but it seems like linux controls this automatically.... when it needs to extra resource it uses all the avaliable power (1.6ghz) to speed things up...

anyways, I was wondering if there is a setting or something that I can tell ubuntu/linux to use 600mhz all the time on battery power? unless I am doing something that'll require 1.6ghz I can just chnage it very quickly...

I'd like itto run at 1.6ghz at all times on AC power too

well?

thx!

---

### Post by 23meg on 2005-12-21
Do```
sudo chmod +s /usr/bin/cpufreq-selector
```
and add the CPU Frequency Monitor applet to your Gnome panel. When you don't want the CPU speed controlled automatically, do```
sudo killall powernowd
```Now you should be able to switch between speeds manually using the applet.

---

### Post by Game_Ender on 2005-12-23
Why does the frequency scaling only have about 4 level of gradation?  I know it has 8, in windows it does.  Is there anyway I can fix this?  I have an Inspiron 600m.

---

