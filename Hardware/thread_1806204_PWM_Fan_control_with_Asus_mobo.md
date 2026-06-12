---
title: "PWM Fan control with Asus mobo"
date: 2011-07-17
forum: Hardware
---

### Post by ceejay on 2011-07-17
I'm trying to build an HTPC - therefore quiet - machine based on an ASUS P8H67-M PRO mobo (P620 CPU). My approach is to use lots of fans running at very low speed, as this should be more efficient in terms of noise/cooling. I have attached 3 PWM case fans (4 pin headers) and the CPU fan (also PWM)... one case fan is directly attached to the CHA_FAN header on the mobo, and the others are connected to the CPU_FAN header using an Akasa PWM splitter cable.

However, when I boot into Ubuntu Linux (11.04) and use sensors-detect, the PWM fans are not being seen - all I get are two CPU core temperatures. This means that I can't use pwmconfig to control the fans as I had intended.

I have installed lm-sensors and fancontrol, and run sensors-detect (saying yes to everything).

Can anyone tell me what I need to do to make these fans visible? I was also hoping to get visibility of mobo voltages as well, and they are not showing up in sensors either.

I have tried this with Q-Fan both enabled and disabled: if "enabled", the fans run at 1000-1100 rpm, which is way too loud (temperatures under 40C). If I disable Q-Fan, which I might guess should make them visible to the OS, then they run much faster and louder!

Comments, anyone?

TIA

---

### Post by ceejay on 2011-07-18
Update: I don't have an answer but have found a thread which at least discusses the problem (among others!). To avoid cross-posting please see [http://ubuntuforums.org/showthread.php?p=11059282#post11059282](http://ubuntuforums.org/showthread.php?p=11059282#post11059282) if you have some help to offer!

Thanks

---

