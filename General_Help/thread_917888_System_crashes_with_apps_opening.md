---
title: "System crashes with apps opening"
date: 2008-09-12
forum: General Help
---

### Post by phaedrus85 on 2008-09-12
AMD Athlon  1000MHz  L2 Cache 256 KB
Memory: 1GB 400mHz
HD: Maxtor 250GB
SONY DVD-RW
Mainboard: VIA VT8378  (KM400/A) Micro-ATX
Video Card: (AGP) nVidia GeForce FX 5700   Video RAM: 256 MB  GPU Frequency: 300 Mhz
Power: 200W

Screen Resolution: Default Setting to 50 Hz (with 53 and 54 also shown to be available)

Hello, I appreciate any help or feedback anyone can give me on my question. I just re-installed Ubuntu 8.04 with all the updates on the hardware with specs listed above. I have the proprietary driver for my nVidia card installed and running, and have removed scripts from running w/o permission with No-Script ad-on for Firefox. 

My problem? I've had this problem for a few months (I thought re-installing Ubuntu would help, but it hasn't) where my system crashes either when running applications under wine or when opening several applications w/o wine. Sometimes I can use my computer for a few seconds; sometimes an hour, but usually I have a system crash at some point very quickly, and my monitor goes black with the message “monitor going to sleep.” I cannot provide a terminal output for the crash when running applications, since the system crashes.

Under System/Preferences/Screen Resolution, it tells me my screen resolution has a refresh rate of 50 Hz (with 53 and 54 also shown to be available to select.)

Also, if I manage to have sound or music playing, when the computer crashes, whatever sound is currently being emitted will replay repeatedly, the same note over and over.

I've ran memtest from a LiveCD and not seen anything unusual-- no errors.

Could it be my low (200W) output from the power supply?

Any ideas on how to approach this, or anything else you need from me to help me figure it out?

Thanks!

---

### Post by Titan8990 on 2008-09-12
I didn't read this post. I Only read: "Could it be my low (200W) output from the power supply?" and "Video Card: (AGP) nVidia GeForce FX 5700 Video RAM: 256 MB GPU Frequency: 300 Mhz".


Your power supply is lower than the minimum requirements of your graphics card.

---

### Post by phaedrus85 on 2008-09-12
I had my suspicions when memtest turned out just fine... 200W is a little low for anything.

---

### Post by Titan8990 on 2008-09-12
Also, as capacitors on a power supply age the power supply looses it's ability to put out the wattage that it once could. This is why many power supply calculators factor is capacitor aging.

---

