---
title: "Sound driver? issue with &quot;Crosshair VII hero Wifi&quot; motherboard"
date: 2021-06-14
forum: Hardware
---

### Post by Drekidegga on 2021-06-14
I have a crosshair VII hero Wifi motherboard. I have always had problems getting the sound to work. Sometimes It works but produces distorted sound, sometimes It doesn't detect when I plug or unplug speakers/headphones.

After doing some digging I think the kernel may be using the wrong driver. Asus says the sound card is "ROG SupremeFX S1220" which I understand is a realtek chipset. But the kernel seems to be using the Intel driver.

0c:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Family 17h (Models 00h-0fh) HD Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 97, IOMMU group 21
        Memory at fcd00000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

---

### Post by Yellow Pasque on 2021-06-14
Intel created the HDA/"Azalia" standard, so the driver is named after them. snd-hda-intel is the correct module.

---

### Post by Drekidegga on 2021-06-15
What could be the problem then? 

Pulse rarely detects when I plug in any speakers/microphone/headphones. And when It does it often only allows S/PDIF out no analog, no surround, Sometimes audio out or microphone in feed gets distorted. Lots of problems and bugs.

The sound card on this motherboard is supposed to be really good so I would really like to use it if I can.

---

### Post by Yellow Pasque on 2021-06-15
The best suggestions I can give are to look at settings in alsamixer, and testing a newer kernel to see if things are better there:
```
alsamixer
```

---

