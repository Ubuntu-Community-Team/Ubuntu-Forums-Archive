---
title: "Laptop temperature"
date: 2010-06-13
forum: Hardware
---

### Post by luismgl on 2010-06-13
I've downloaded XSensors but it doesn't work at all, is there any other software that you guys can recommend? 
Also, before having ubuntu, my temp1 temperature was around 50-60ºC and the cores around 30-45ºC, I have a feeling that its slightly higher with ubuntu, is it normal?

---

### Post by sgosnell on 2010-06-13
Sensors should be in the kernel.  Configure it with ```
sudo sensors-detect
``` then just run 'sensors' when you want readings.

---

### Post by limestone on 2010-06-13
I had that before to, and my cpu-fan went bananas.. I installed my graphic card drivers and the laptop got cooler.

---

### Post by luismgl on 2010-06-13
> **pont.andersson said:**
> I had that before to, and my cpu-fan went bananas.. I installed my graphic card drivers and the laptop got cooler.

Haven't though of searching for drivers yet, since everything is pretty much working well, expect the temperatures, although I have a (lame) integrated graphic card, so dunno how much I would need drivers.
I'll look around to see what I find, thanks.

---

### Post by yossell on 2010-06-13
Adding the cpu frequency scaling monitor utility to the gnome panel and setting it to 'on demand' or 'powersave' rather than performance ensures the chip runs slower when idle and might help. Also I've found the program `powertop' can help run the computer cooler.

---

### Post by luismgl on 2010-06-15
Sorry Ive completely neglected this. I've installed it.

---

### Post by yossell on 2010-06-15
you need to run it from a terminal. It'll be more helpful if you run it as root. 

I.e. bring up a terminal and type: sudo powertop

---

