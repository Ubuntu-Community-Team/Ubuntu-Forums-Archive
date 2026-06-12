---
title: "Where is Im-sensors"
date: 2008-11-23
forum: General Help
---

### Post by ozguitarplayer on 2008-11-23
Hi,
I have loaded Im-sensors however I don't know where/how to find Im in order to find fan speed and temp, can some one tell me where to find it please.

---

### Post by earthpigg on 2008-11-23
in terminal, type:

```
sensors
```

:)

---

### Post by ozguitarplayer on 2008-11-23
thanks...I get this message...

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

...synaptic manager says the sensors are loaded...does this mean the kernel driver mentioned above?

---

### Post by doas777 on 2008-11-23
try running the command ```
sudo sensors-detect
```
then run sensors again.

theres a panel applet that displays temps from lm-sensors, if you google it you'll find a tutorial on getting it installed.

good luck,
franklin

---

### Post by drs305 on 2008-11-23
I believe you have to run *sudo sensors-detect* to probe your system for the applicable sensors before the app will function properly.

There is a gui app, gkrellm, that can use the same data.

---

### Post by Yellow Pasque on 2008-11-23
> synaptic manager says the sensors are loaded...does this mean the kernel driver mentioned above?
Synaptic just tells you whether the package is installed.

---

