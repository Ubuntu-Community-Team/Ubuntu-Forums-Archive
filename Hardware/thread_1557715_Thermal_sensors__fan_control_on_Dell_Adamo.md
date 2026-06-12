---
title: "Thermal sensors / fan control on Dell Adamo"
date: 2010-08-21
forum: Hardware
---

### Post by Ole_M on 2010-08-21
There appear to be five thermal sensors in the Dell Adamo. Two are for the two CPU cores. What are the other three assigned to?

How can I tweak the fan control? The fan state is binary (on/off) so far. A finer control would be nice.

Ole

---

### Post by Ole_M on 2010-09-04
bump

Dell cannot tell me what the other 3 thermal sensors are for, because it is a "company secret". Yeah. Sure. Strange way to admit that they have no clue.

So the questions persist. Any ideas about the sensors or the fan control?

---

### Post by Lateralis on 2010-09-04
Setting up fan control is relatively straightfoward - if a little involved - in Linux operating systems.  

I would explain how to do everything step-wise but there are a few good guides out there, including this one: [http://wiki.archlinux.org/index.php/Fan_Speed_Control](http://wiki.archlinux.org/index.php/Fan_Speed_Control).  Follow the instructions contained in this thread and you should have fan control. 

I suppose at this point I should echo the warning contained in the link.  What you will be doing is fiddling with your PC's cooling, specifically turning off the CPU fan, albeit for a few seconds.  You do this at your own risk. 

As for what the other sensors are for... there can be, and often are temperature sensors just about everywhere in a PC - hard drives, northbridge, southbridge, graphics card, CPU cores etc...  A question for you: how did you determine what sensors you have in your compute?

---

### Post by jcolyn on 2010-09-04
> **Lateralis said:**
> A question for you: how did you determine what sensors you have in your compute?

```
sensors
``` at the terminal if you have lm-sensors installed and have run ```
sensors-detect
``` and answered yes to all of the questions..

---

### Post by Lateralis on 2010-09-05
I know that jcolyn... I was asking he how he detected his sensors.  If Ole knew about lm-sensors then he was only a commands away from having fan control and would probably have stumbled upon a web guide.  So I was just curious as to whether Ole did use lm-sensors to divine how many temperature sensors he has or some other method.  (Manual, psychic powers, other Dell users who said there are 5 sensors etc...)

---

### Post by Ole_M on 2010-09-05
Aye, some activity here. :D Thanks for the replies.

The link about the fan-control looks very promising. I will try it the next few days. Seems I searched not thoroughly enough for this problem. My apologies.

As for the sensors: Psychic powers it is. Ok, not quite. I tried the "sensors" approach, among others. The two core-sensors are labeled as such. The other three are called meaningfully temp1/temp2/temp3. Besides that, I browsed ```
/sys/class/hwmon
``` and ```
/sys/bus/i2c/devices
``` to look for these sensors manually. This, however, did not reveal new information.

Ole

---

