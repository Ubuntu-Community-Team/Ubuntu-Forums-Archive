---
title: "Laptop does not boot when keyboard is connected"
date: 2024-03-15
forum: Hardware
---

### Post by di-mk1 on 2024-03-15
Hi,

fresh installation of Ubuntu 22.04 in a Lenovo T14 laptop. I have a Keychron K8 keyboard and if the keyboard is connected via USB the laptop does not boot. It goes into an endless loop (start -> show Lenovo logo -> black screen -> restarts). When I disconnect the keyboard all goes fine (I can reconnect it afterwards with no issues). Can someone suggest a few things to look into? Can I collect some sort of logs to start investigating this?

---

### Post by yancek on 2024-03-15
Do you have multiple USB ports o this computer?  Do you get the same results if you use other USB ports?  Log files are in the /var/log directory and I would start with the boot.log or dmesg files to look for problems.

---

