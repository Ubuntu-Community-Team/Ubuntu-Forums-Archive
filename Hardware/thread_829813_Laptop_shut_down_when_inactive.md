---
title: "Laptop shut down when inactive"
date: 2008-06-15
forum: Hardware
---

### Post by bclemon on 2008-06-15
Hi, my laptop shuts down when I leave it (guess 15-20 min) , I have checked the "System -> Pref -> Power Management" It shall not shutdown, go to sleep, hib or anything else. Any ideas, where to look? It is Ubuntu x86 8.04.

Thanks in advance
Fleming

---

### Post by lswb on 2008-06-15
If this is an older laptop (maybe some not so old?) it may have BIOS hardware control sleep settings. Do you know if the laptop uses APM or ACPI? Does it shutdown when plugged in, or only when running on the battery?

---

### Post by bclemon on 2008-06-15
Hi, it is nothing in bios, and it shut down when it is connected to the power. It is a pretty "new" two years old computer and I don't know if it is APM or ACPI, how do I check? 

Thanks in advance
Fleming

---

### Post by lswb on 2008-06-15
It certainly uses ACPI if it is only 2 years old, APM was phased out something like 6 years ago. Still, there are some known ACPI related issues with specific models. Have you tried a google search with your laptop make and model and something like "linux sleep acpi" in the search terms? What version of ubuntu are you running? Have you made any changes to the power management software or is it just form the original installation? IIRC some versions had power management setting available in the screensaver menu.

---

### Post by sdennie on 2008-06-15
You might be able to solve this using various boot options.  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions).  There was a similar thread to this a while back and that link sorted out their problems.

---

### Post by Odrodzona-Sarmacja on 2008-06-16
Also I noticed there are two screensavers (gnome and xfce), which both come with different power settings... I uninstalled them both...

---

### Post by entercomp on 2008-09-07
I am having the same problem with a 8.04 on a Lenovo 3000 v100. If on AC power or battery and the laptop is inactive for about 10 to 20 minutes it requires a power on. Any help on this yet? tried a couple of threads that did not work. All power options are set to NEVER NEVER in system preferences power management.

---

