---
title: "Video Driver Version Command"
date: 2009-01-17
forum: Hardware
---

### Post by xx.canes.rites on 2009-01-17
Hello,

Quick question, what's the command for me to check which video driver I currently have installed? I installed the new NVIDIA 180.22 beta driver and I just want to check to make sure that it was installed. Thank you :)

---

### Post by xx.canes.rites on 2009-01-17
Okay I've found a way that it will list the driver version. ```
dmesg | grep NVIDIA
```

That seemed to work for me, but I had an issue at first because i typed NVIDIA in lower caps like this, 'nvidia' and it didn't show me the driver version, so I retyped than it finally showed it to me.

---

### Post by trindy on 2009-02-25
"dmesg | grep -i nvidia", the "-i" tells grep command to ignore case.

---

### Post by AaronP_ on 2009-02-27
To do it more reliably, try "cat /proc/driver/nvidia/version" or "nvidia-settings -q NvidiaDriverVersion".

---

