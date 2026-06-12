---
title: "Strange work fan Dell e6530"
date: 2017-01-28
forum: Hardware
---

### Post by woj2 on 2017-01-28
I have laptop dell e6530, I installed ubuntu 16.04 and I think fan works strange, that is constantly spinning, sometimes slows down for 1 sec and accelerates again, result of sensors command:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +65.5°C  (crit = +107.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +56.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +55.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +53.0°C  (high = +87.0°C, crit = +105.0°C)
Core 2:         +55.0°C  (high = +87.0°C, crit = +105.0°C)
Core 3:         +56.0°C  (high = +87.0°C, crit = +105.0°C)

dell_smm-virtual-0
Adapter: Virtual device
Processor Fan: 3163 RPM
CPU:            +56.0°C  
Ambient:        +43.0°C  
SODIMM:         +43.0°C  
GPU:            +54.0°C

```
is there any possibility to stabilize, reduce the fan speed? I would add that BIOS don't have fan control option and is upgraded to newest version, when laptop starts the fan is working fine and quietly, after logging into Ubuntu fan starts work faster and more loudly.

---

### Post by wildmanne39 on 2017-01-28
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by jan-pedryc on 2017-01-28
On a Dell Workstation (T5500) with similar problems I used the i8kutils and it worked fine for me:
> sudo apt-get install i8kutils

or the source from [github]("https://github.com/vitorafsr/i8kutils").

I could control the fan speed of two main fans by:
> sudo i8kfan 2 2
Where 2 was the highest possible value.
For example:
> sudo i8kfan 2 1
First fan at full speed, second one - half of the speed.

---

### Post by woj2 on 2017-01-28
In my laptop this command not works sudo i8kfan, is normal temperature 55 C when no one aplication is running?

---

### Post by jan-pedryc on 2017-01-28
[Here]("https://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/") you can find a detailed instruction how to enable the i8k driver on Dell Laptops. Additionally, there is a screen-capture of the [FONT=courier new]sensors[/FONT] output, where the temperatures are similar to yours.

---

