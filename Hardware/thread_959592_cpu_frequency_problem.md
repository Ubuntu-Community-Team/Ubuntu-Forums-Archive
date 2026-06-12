---
title: "cpu frequency problem"
date: 2008-10-26
forum: Hardware
---

### Post by Elric27 on 2008-10-26
Hi. My laptop is a HP 6715s, with an amd64. Powernowd was the service responsible for scaling the cpu. I could also set it through the cpufreq-selector applet. The thing is that I uninstalled powernowd cause it was getting sometimes killed on boot, and thought of replacing with cpudyn or cpufreqd. To my surprise, I disabled the service powernowd (not removed) and I can still set the freq with the applet, and without any of the services aforementioned. Why is this? Does the applet interact directly with the kernel with no need of the other services? Am I fine with none of this services? My cpu is fine, so far. Should i try cpudyn?
Thanks

---

### Post by ddrichardson on 2008-10-27
From what I understand, powernowd is not loaded unless the ondemand governor fails. There's a bug thread along those lines [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/223812"). I find cpudyn is OK though.

---

