---
title: "ubuntu and CPU/fan scaling"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by slavik on 2006-02-11
I have the CPU frequency in a bar. It always says 1.8GHz (actual rated speed of the CPU) and doesn't scale it down to 800MHz (or whatever it has to do).

The CPU is a Sempron 3000+ (1.8GHz) in a Compaq V2000Z

The CPU fan also seems to be turned up at higher temperatures when my laptop is really warm and the fan iss till very silent ... is there a way to adjust this? (and the cpu scaling)

---

### Post by Sutekh on 2006-02-11
You are able to use the Scaling Applet (in your panel) to choose both the frequency of the processor and the 'governor', which governs the scaling behaviour of the processor.  

```
sudo chmod +s /usr/bin/cpufreq-selector
```
Will allow you to change these settings by left-clicking the 'chip' on your panel.

Not sure about controlling the fan though.

---

### Post by slavik on 2006-02-11
got it to work, but how can I set up so that it automatically throttles the CPU (based on CPU usage?)

basically, my CPU supports 3 frequencies: 1.8GHz, 1.6GHz and 800MHz ... I want it to throttle based on CPU usage at the various stages (if CPU usage reaches 90% in 800MHz, the go upto 1.6GHz, if it goes over 90% there, go to 1.8GHz. If CPU usage at 1.8GHz is below 80% then go down to 1.6GHz, if it is below 50% there, then go down to 800MHz). Any ideas on this?

---

### Post by Greg2 on 2006-02-11
[QUOTE=slavik]got it to work, but how can I set up so that it automatically throttles the CPU (based on CPU usage?)[/QUOTE]
You can select the ondemand governor from the applet. I’m not sure if or how you can set the ‘specific parameters’ you want?

---

### Post by slavik on 2006-02-11
does the governor scale the CPU speed automatically?

---

### Post by Greg2 on 2006-02-11
[QUOTE=slavik]does the governor scale the CPU speed automatically?[/QUOTE]
My laptop has an AMD Sempron 2800 1.6 GHz, and it automatically scales it from 800 MHz to 1.6 GHz when the system needs it.

---

