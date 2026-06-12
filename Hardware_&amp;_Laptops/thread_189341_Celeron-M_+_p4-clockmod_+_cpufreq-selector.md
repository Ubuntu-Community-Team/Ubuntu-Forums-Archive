---
title: "Celeron-M + p4-clockmod + cpufreq-selector"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by lzap on 2006-06-05
Hi,

when I boot my ThinkPad R50e the cpu frequency applet shows the dynamic scaling of the frequency (even when AC is on). It means the govenor is set to "ondemand". I want to have it on "performance" when AC is on.

Is there any chance to automaticaly switch this? I do not want to use cpufreqd, it didnt work for me on my Gentoo system...

---

### Post by lzap on 2006-06-05
It seems I use powernowd. It cannot check the batteries. Is it possible to create some scripts? I found the /etc/acpi/events directory, seems nice. How to use them?

ps - is there any way to disable the Fn+F4 (sleep) button? Since the sleep is not working properly now, I do not want it. I sometimes press it when I want Ctrl+F4 and my laptop hangs...

---

### Post by lzap on 2006-06-05
Oh I found ac.d and battery.d directories. I will put sh scripts there. But I am not sure about the state after boot. I will check it out...

---

### Post by snegovick on 2008-07-20
thanks for ideas

---

