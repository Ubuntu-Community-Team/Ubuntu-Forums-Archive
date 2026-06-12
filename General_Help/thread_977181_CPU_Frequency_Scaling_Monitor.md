---
title: "CPU Frequency Scaling Monitor"
date: 2008-11-10
forum: General Help
---

### Post by sci-fi guy on 2008-11-10
I have a questions about the CPU Frequency Scaling Monitor applet for gnome-panel: What does the "Conservative" setting do? "Powersave", "Performance", and "On Demand" are pretty obvious, but I can't figure out the last one.

---

### Post by Ocxic on 2008-11-10
conservative is like on demand but sets the threshold higher before upping the cpu speed

---

### Post by sci-fi guy on 2008-11-11
Thanks. Any idea how I can change the setting and have it persist after reboots?

---

### Post by Ocxic on 2008-11-11
sudo chmod +s /usr/bin/cpufreq-selector

that will allow you to use the panel applet to change the settings, i think is should persist after reboot but not sure.

---

