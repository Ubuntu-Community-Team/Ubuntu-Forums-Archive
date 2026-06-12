---
title: "Desktop Ubuntu Karmic CD on Laptop, runs hot/fan"
date: 2010-05-21
forum: Hardware
---

### Post by brevardo on 2010-05-21
I just recently installed Ubuntu Karmic ( desktop version ) on my Dell Latitude D620. I mailed away for the CD initially for my desktop and decided to install it on my Laptop. It seems to run great as far as just having a clean install. The only issue that I have noticed is that it seems to work real hard very fast. Meaning I'll only have it on for a short period of time and the fan starts getting very loud. It didn't do this when I had Windows XP on this laptop. It's actually shut down a couple of times as it seemed to get over heated. Is this normal? I have a feeling that I need to change a setting as it's probably not getting as hot as the operating system is detecting. I'm wondering if it's doing this because it thinks it's a desktop since Ii used the desktop install cd? Please advice as everything else runs great!   Thanks

---

### Post by Tclarkie on 2010-05-21
hi can you please run "sensors" in terminal and post the output

---

### Post by brevardo on 2010-05-22
I ran sensors and apparently it hadn't been installed yet so I just now installed it and here is what I got ( below ) Do you think because I didn't have Sensors installed could have caused the problem? 

ldconfig deferred processing now taking place
richard@richard-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.5°C  (crit = +126.0°C)                  

richard@richard-laptop:~$

---

### Post by Tclarkie on 2010-08-14
are you sure thats not your optical drive running fast

---

### Post by JBAlaska on 2010-08-14
Since your CPU temp seems normal, I'm guessing it's your Graphics chip that may be getting hot.

Have you installed the restricted hardware drivers for your  NVIDIA Quadro NVS 110M?

If so you can go to System, Administration, NVIDIA X server settings and check the temp under Thermal Settings.

---

