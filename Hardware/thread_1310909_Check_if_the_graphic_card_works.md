---
title: "Check if the graphic card works"
date: 2009-11-02
forum: Hardware
---

### Post by drorata on 2009-11-02
Hallo all,

I am running Ubuntu 8.04 on a ThinkPad x61s, and I suspect that the graphic card is not working properly. The reason of this suspicion is the following.

I am using a lot a software called JavaView - when ever I load a model and simply rotate it, I can see (in the system monitor graph) that the CPU usage jumps up. Another example; after a screen saver was running, and I see again the CPU usage graph, I can see that while the screen saver was running the CPU usage was very high.

I don't know even where to start... How can I tell if my graphic card works? Or is everything is done by the CPU.

Any ideas?

Thanks in advance and have a nice week,
Dror

---

### Post by howcanireachthesekids on 2009-11-02
do you have an ATI graphic card ?
ATI doesnt really like Linux...:p
oh and did you try installing the driver from the Hardware Drivers option ?

---

### Post by drorata on 2009-11-02
As far as I know I have an Intel-Graphic card. I did not install anything specific or special. The only change I made was in xorg.conf:

```
Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        32000
        Option          "UseFBDev"              "true"
EndSection
```

where I've set the driver to be "intel".

---

