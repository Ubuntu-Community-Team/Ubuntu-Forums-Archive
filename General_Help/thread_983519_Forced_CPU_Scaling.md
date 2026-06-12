---
title: "Forced CPU Scaling"
date: 2008-11-15
forum: General Help
---

### Post by th89 on 2008-11-15
Hey all, I am having a problem with a forced CPU scaling on my laptop. This only happens when I switch to battery power. After I plug into AC, it still will not cycle up the CPU for several minuets (10-15ish), and even then sometimes it wont. Sometimes I have to restart plugged in to get my CPU Frequency back up to full speed. I have a 2.1GHz processor, and it always force scales it to the lowest setting, 800MHz. Any suggestions? I'm running Intrepid (8.10).

---

### Post by dcstar on 2008-11-15
> **th89 said:**
> Hey all, I am having a problem with a forced CPU scaling on my laptop. This only happens when I switch to battery power. After I plug into AC, it still will not cycle up the CPU for several minuets (10-15ish), and even then sometimes it wont. Sometimes I have to restart plugged in to get my CPU Frequency back up to full speed. I have a 2.1GHz processor, and it always force scales it to the lowest setting, 800MHz. Any suggestions? I'm running Intrepid (8.10).

Add the CPU scaling applet and use it to change this manually, and do this to give root privileges to the cpufreq-selector applet:

```
sudo dpkg-reconfigure gnome-applets
```

---

### Post by th89 on 2008-11-15
I already have the applet on my taskbar, and can change the frequency when I want - If im plugged in. However, when it is on battery power, I cannot change the frequency. Its not just in monitor mode, becuase like I said, I am able to change it if im plugged in or 15 mins after plugging in.

---

