---
title: "Laptop Fan Scaling?"
date: 2008-11-01
forum: Hardware
---

### Post by rhcm123 on 2008-11-01
I have a toshiba m55 laptop. A very rugged and reliable piece of hardware, i have had it for quite some time and am very happy with it.

However, I do have a 1 problem when using ubuntu.
When I wiped my harddrive several months ago (i do this every couple years - it dramatically speeds up boot times and clears out junk in ways nothing else can) i created 3 partitions.
1: 75 gb: windows & windows files
2: 4.5 gb: ubuntu
3: 0.5 gb: swap

This sped up my machine very well.
However, accompanying this speed came new features. This is not a bad thing; For example, when i was running ubuntu off wubi, i did not have the speed capabilites to use the advanced hardware effects. Now i do.

But this creates 1 problem that did not exist with wubi. Fan scaling.
On windows, my computer senses if it is growing too hot and scales up the fan to compensate.
But in wubi, the fan is always on low, which is creating overheating problems. My computer is freezing up and crashing now, and when i put my hand by the vent, it is burning hot -overheated.

Does anybody know how to change the fan speed in ubuntu?

---

### Post by ardvark71 on 2008-11-01
Hi...

Try installing "lm-sensors" in Synaptic and then go to this page...

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29)

for instructions on changing fan speeds as well as how "to detect CPU temperature, fan speeds and voltages." The guide was written for Feisty but it might work for your version.

Hope this helps. :) 

Best Regards...

---

### Post by rhcm123 on 2008-11-02
Thanks... it dosen't detect my fan though... pity.

---

### Post by ardvark71 on 2008-11-02
> **rhcm123 said:**
> Thanks... it dosen't detect my fan though... pity.

Hi...

It might be a long shot, but would this thread at this other site be of help...

[http://www.computing.net/answers/linux/ubuntu-acpi-and-cooling-fans/29696.html](http://www.computing.net/answers/linux/ubuntu-acpi-and-cooling-fans/29696.html)

Or here...

[http://ubuntuforums.org/archive/index.php/t-41927.html](http://ubuntuforums.org/archive/index.php/t-41927.html)

Best Regards...

---

### Post by rhcm123 on 2008-11-05
no, those don't work either :( .Sorry, but thanks for helping!

---

### Post by brandon88tube on 2008-11-05
Yeah, I need some solution as my fans almost never turn on until it gets to the point where I could cook some food on side ports.

---

