---
title: "Dell Inspiron heating up on Ubuntu 9.10"
date: 2010-04-17
forum: Hardware
---

### Post by talonfast on 2010-04-17
Hi,
I have a Dell Inspiron that heats up on Ubuntu 9.10. Windows XP, Mandriva, or even 8.04 doesn't have this problem. I am a beginner to problems and could use some help.

Thanks,
Talon

---

### Post by bcbc on 2010-04-17
What sort of temperatures are you getting? My inspiron 6400 is running about 50C.

---

### Post by wilee-nilee on 2010-04-17
There is a fan control setup for dells, install gkrellm-i8k, just search for gkrellm in synaptic. Then follow this set of instructions.
[http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

If you just use the 1-4 instructions without the script, gkrellm when you turn on the i8k plugin will allow you to adjust your fans speed and start temperature. You can then in startup programs add gkrellm just by putting gkrellm in the command and it will be running on boot up.

---

### Post by bcbc on 2010-04-17
I just switched to XP - I don't have a tool to read the cpu temp, but it feels just as hot. Either way - I'm not using it directly on my lap.

---

### Post by wilee-nilee on 2010-04-17
> **bcbc said:**
> I just switched to XP - I don't have a tool to read the cpu temp, but it feels just as hot. Either way - I'm not using it directly on my lap.

In case you want to know there is a .exe version of the same i8k fan control. I have used it in Ubuntu and XP.
[http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)

---

### Post by talonfast on 2010-04-18
I don't know the exact temps. But I can say that I could fry eggs on the touchpad lol. I'm upgrading to 10.04 as I type this. So hopefully it'll cool down my laptop. I think it's running at a good 70-80. And it shuts itself off intermittently when it gets hot.

---

### Post by bcbc on 2010-04-18
on my comp it's here:
```
cat /proc/acpi/thermal_zone/THM/temperature
```

---

### Post by talonfast on 2010-06-26
hey guys,
sorry its been awhile, but ive had school and stuff. i tried the above command but it said that it couldnt find that file or directory. any more ideas?

---

