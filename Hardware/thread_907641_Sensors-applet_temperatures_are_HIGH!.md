---
title: "Sensors-applet temperatures are HIGH!"
date: 2008-09-01
forum: Hardware
---

### Post by Envergure on 2008-09-01
The sensors-applet on my GNOME Panel is reading GPU = 75°C and CPU = 62°C, and i think that's simply not true.  The outside of the case can't be more than 35.

Sometimes it reads GPU > 55°C immediately after booting from room temperature (which is about 22-24°C right now).


1)  What's the best way to verify the numbers sensors-applet is giving me?
2)  Why would they be wrong?
3)  How can i get it to run cooler?


My computer is probably an Acer Aspire 5920 with a Core 2 Duo T5550 and a GeForce 8600M GS 256MB.  It may also be an Aspire 5920_G_.

---

### Post by doas777 on 2008-09-01
> **Envergure said:**
> The sensors-applet on my GNOME Panel is reading GPU = 75°C and CPU = 62°C, and i think that's simply not true.  The outside of the case can't be more than 35.

Sometimes it reads GPU > 55°C immediately after booting from room temperature (which is about 22-24°C right now).


1)  What's the best way to verify the numbers sensors-applet is giving me?
2)  Why would they be wrong?
3)  How can i get it to run cooler?


My computer is probably an Acer Aspire 5920 with a Core 2 Duo T5550 and a GeForce 8600M GS 256MB.  It may also be an Aspire 5920_G_.

the GPU temp is most likely correct. My NVIDIA cards seem to run between 70 and 96, both in laptops, desktops, using lm-sensors on ubuntu or speedfan in windows. 

in terms of your Core2, I had to do some thermal scaling in the last version of speedfan for my E6850. I can't tell you if the temp is correct, but if you are running a laptop then it;s not out of the realm of possiblity. when I'm running Civ4 on my HP laptop, my GPU/CPU get above 70, at which point I shut down to let it kool.

this is what sensors shows me without anything running:
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +47.0°C                                    
Core0 Temp:  +41.0°C                                    
Core1 Temp:  +37.0°C                                    
Core1 Temp:  +37.0°C    

hope that helps,
frank

---

### Post by doas777 on 2008-09-01
oh, forgot to mention, if you are running a desktop there is a lot you can do to fix thermal issues. with laptops however thats not the case. all you can do is keep it clean, and maybe open it up and blow it out. don't run it unless it is on a hard flat surface (not on carpet or on a bed), and mabey get a cooling panel/tray.

with a desktop, replace the fan/heatsink on your vid card, remount your CPU heatsink with new thermal paste (get the silver kind, and use only exactly the right ammount), or get a better one. also look at your air flow and make sure all your fans are working well and are clean. add new fans as needed, and ensure you have a clear air flow pattern. I was able to drop a Pentium D by 20 some degrees C just by installing my innards in a new larger case.

hope that helps.

---

### Post by mrmorris on 2008-09-01
75 sounds about right, the same as my Nvidia GPU. The CPU sounds a bit high, although with small fan / limited air flow it could very well be true. In contrast, my E6750 shows a temperature of 46c (and both cores around 30c)

---

### Post by mellowd on 2008-09-01
Could be right. My 8800gt runs at 78C on average on startup

---

### Post by Aruhn on 2008-09-02
In my Laptop, the Geforce 8400M GPU has mostly a temperature at 76°.

---

