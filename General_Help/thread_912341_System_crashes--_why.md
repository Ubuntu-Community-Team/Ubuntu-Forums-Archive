---
title: "System crashes-- why?"
date: 2008-09-06
forum: General Help
---

### Post by phaedrus85 on 2008-09-06
AMD Athlon  1000MHz  L2 Cache 256 KB
Memory: 1 GB
HD: Maxtor 250GB
SONY DVD-RW
Mainboard: VIA VT8378  (KM400/A) Micro-ATX
Video Card: (AGP) nVidia GeForce FX 5700   Video RAM: 256 MB  GPU Frequency: 300 Mhz

Screen Resolution: Default Setting to 50 Hz (with 53 and 54 also shown to be available)

Hello, I appreciate any help or feedback anyone can give me on my question. I just re-installed Ubuntu 7.04 with all the updates on the hardware with specs listed above. I have the proprietary driver for my nVidia card installed and running, and have removed scripts from running w/o permission with No-Script ad-on for Firefox. 

My problem? I've had this problem for a few months (I thought re-installing Ubuntu would help, but it hasn't) where my system crashes either when running World of Warcraft under wine or when opening several applications. I installed wine from source and WoW as described in this link [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft), adding  SET gxApi "opengl" SET ffxDeath "0"
SET ffxGlow "0" SET M2UseShaders "0" which dramatically improved my performance. I have sound. 
Sometimes I can play WoW for a few seconds; sometimes an hour, but usually I am have a system crash after a few minutes of playing, and my monitor goes black with the message “no output detected.” I cannot provide a terminal output for the crash when running WoW, since the system crashes.

Under System/Preferences/Screen Resolution, it tells me my screen resolution has a refresh rate of 50 Hz (with 53 and 54 also shown to be available to select.)

I don't know how to fix this; in the past when my computer would crash when I was surfing the net or opening an application, and not playing WoW, it made me think it had to do with processing speed, memory, or the display. However, the past few days since I re-installed Ubuntu 7.04, I've not had any problems with the system crashing because of opening applications.

Any ideas on how to approach this, or anything else you need from me to help me figure it out?

Thanks!

---

### Post by Sycron on 2008-09-06
Why are you using 7.04 ? It's outdated that version. Can you go with Ubuntu 8.04 Hardy Heron to benefit the latest software version available ?

You may try xubuntu on your computer, because it's a bit slow.

---

### Post by wolfen69 on 2008-09-06
i suggest doing a memory test. pop in a live cd and choose memtest at the first menu.(let it run for a while) bad memory can cause crashing. if a reinstall did not fix it, chances are your hardware is at fault.

---

### Post by phaedrus85 on 2008-09-06
Its been updated to 8.04; I should have specifically included that in the aforementioned updates.

---

### Post by Sycron on 2008-09-06
> **wolfen69 said:**
> i suggest doing a memory test. pop in a live cd and choose memtest at the first menu.(let it run for a while) bad memory can cause crashing. if a reinstall did not fix it, chances are your hardware is at fault.

Correct.

---

