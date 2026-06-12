---
title: "lm-sensors problem"
date: 2024-09-28
forum: Hardware
---

### Post by kap-franje on 2024-09-28
Hi, after sintalling lm-senors, I started to get "[COLOR=#0066CC][FONT=RedHatText]Failed to start systemd-modules-load.service - Load Kernel Modules.[/FONT][/COLOR]" sensors command still show some temperatures (for example the temperatures of my 4 cores). I remember there is a fix for it, but I forgot it. I had to reinstall ubuntu server, and started to have this problem again.

---

### Post by Yellow Pasque on 2024-09-29
I'm guessing you ran sensors-detect and it put modules in /etc/modules that won't load. it87 is a common cuplrit. In fact, I answered a very similar question 5 years ago, almost to the day: [https://ubuntuforums.org/showthread.php?t=2428070](https://ubuntuforums.org/showthread.php?t=2428070)

---

