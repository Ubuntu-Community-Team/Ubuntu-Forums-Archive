---
title: "Manual CPU scaling"
date: 2009-06-05
forum: Hardware
---

### Post by Ferrat on 2009-06-05
Ok I've gotten CPU scaling working without any problems but it's only working when automatically set from /etc/cpufreqd.conf, for some reason it doesn't work manually tried using 
```
cpufreq-selector -f 1067000
```
which every howto says should work ( yes 1067000 is one of my 4 possible speeds) 
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1600000 1333000 1067000 800000
```

It's really annoying cause I want to be able to set the speed manually sometimes overriding the auto setting, worst case remove the auto setting so I can do it just manually. 
Got the gnome-applet "working" but this too fails to set the speed manually, I'm guessing it's a problem with the auto setting overriding manual settings or something? 
Also the applet can change governor 
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance 

```
but for some reason this doesn't change anything else, CPU speeds that show up in the applet as available are non-responsive unless it's the speed currently running, then it gets selected and the permissions for the applet and cpufreq-selector is fixed btw. 

Really bummed out that scaling works but I can't control it :/ 

Anyone got any ideas?

---

### Post by Ferrat on 2009-06-06
shameless bump :P

---

### Post by Ferrat on 2009-06-07
No one that can help me with this? no one knows why I can't set it manually??

---

