---
title: "Overclocking monitoring software"
date: 2008-07-02
forum: Hardware
---

### Post by ingrid_ozikem on 2008-07-02
Overclocking forums on the net are a dime a dozen but all talk about Windows (though I bet many of those people use linux as well). 

One should always overclock using BIOS but one needs good reliable monitoring software -- to monitor voltages, frequency and temperature.

Are there Ubuntu equivalents of CPU-Z and other such Windows programs? (CPU-Z through Wine doesn't work). The frequency is easy to monitor but someone please help me monitor,

1. temperature -- how reliable is your method? How does it work physically?

2. voltages (RAM and CPU)

---

### Post by kevmitch on 2008-07-02
I've found the most comprehensive and easy to use tool is gkrellm. You'll likely have to configure it a little, though this isn't too hard since it can all be done within the GUI. Just compare the values with the BIOS if you can to ensure you're looking at the correct things.

---

### Post by ingrid_ozikem on 2008-08-02
I'm using Gkrellm and can see that it reports temperatures and voltages. But how reliable is the reading for voltage?

I see many postings all over the net about Core Temp vs Real Temp etc for Windows -- how some methods are misleading and others not. 

I'd love to hear a bit on different temperature measuring methods in Ubuntu and their reliability. Gkrellm seems to use lm-sensors.

---

