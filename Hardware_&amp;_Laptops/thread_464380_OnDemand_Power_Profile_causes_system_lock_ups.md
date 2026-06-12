---
title: "OnDemand Power Profile causes system lock ups"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Death_Sargent on 2007-06-04
the ondemand power profile causes system lock ups

is there a way to edit the gnome-power-manager ondemand profile so perhaps it does not cause problems

---

### Post by Death_Sargent on 2007-06-05
push and clarify

What i mean is what files govern the powernowd and or cpufreqd powerprofiles.

---

### Post by Death_Sargent on 2007-06-05
Yet another push 

maybe my timming is just bad but i have yet to get anyone responding and this is the second thread i have made

---

### Post by Hisstareia on 2007-06-07
Try going into **gconf-editor** and checking the box next to: 

> 
apps>gnome-power-manager>show_cpufreq_ui.

Next time you go into power manager, you should see a new box allowing you to adjust CPU frequency. I believe you can also do it from gconf itself through the **cpufreq_ac_policy** and the **cpufreq_battery_policy**, which are also in apps>gnome-power-manager.

---

### Post by Death_Sargent on 2007-06-07
close but no cigar. I mean chage the actuall policies that these things are related to.

---

