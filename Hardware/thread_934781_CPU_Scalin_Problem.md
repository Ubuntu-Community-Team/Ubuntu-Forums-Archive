---
title: "CPU Scalin Problem"
date: 2008-09-30
forum: Hardware
---

### Post by jcathey on 2008-09-30
I just bought a new laptop: Toshiba M305D-S4830, with turion x2 2.1ghz processor, 4gb ram, 250gb HD. I installed kubuntu 8.04 on it and finally got everything working on it (network card and wireless not work out of b ox.) I have all hardware working now and the system absolutely flies. The problem is that the cpu never calms down even if i am doing nothing (fan is always on running hot, and battery life is non-existent). When right clicking on the battery icon in the system tray, i do not have the normal options to set to best performance, etc, and the cpu frequency does not report. If i run the command "powernowd" then the frequency is reported at 2100Ghz for both processors. The options are still not available and the fan is still trying to blow the walls down. If this thing doesn't stop blowing i will have to find a hooker name for my laptop. Any ideas would be greatly appreciated. It would be nice to actually be able to use my laptop as a laptop without worrying about my future kids safety.

Thanks,

Jeremy

---

### Post by ajc347ha on 2008-10-02
Hey i do not know about the scaling problem but i do have a question for you though how did you get your network devices to work because i am trying to find resources on the subject because i have recently just bought the same laptop that you have. If you could tell me how you did it or direct me to the sources you used that would be greatly appreciated...ajc

---

### Post by Yellow Pasque on 2008-10-02
```
sudo apt-get install cpufrequtils
sudo cpufreq-set -g ondemand
```

---

