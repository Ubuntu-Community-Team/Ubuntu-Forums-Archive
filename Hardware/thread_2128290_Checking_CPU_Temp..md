---
title: "Checking CPU Temp."
date: 2013-03-22
forum: Hardware
---

### Post by NNJRob on 2013-03-22
I hope this is the right section for this....

Is there some way to find out what temperature my cpu is generating? Possibly, something I can run from the terminal? I checked my panel options (XFCE) , and if there's one there,,I missed it. :oops:

---

### Post by stinkeye on 2013-03-22
Try **psensor** (I think it needs lm-sensors for cpu temp)

and/or

Have a look [**_[COLOR="#B22222"]here[/COLOR]_**]("http://conky.pitstop.free.fr/wiki/index.php5?title=Using_Sensors_%28en%29") for using sensors.
The linked guide is for conky but the first part shows how to set up, once lm-sensors is installed.

Basically 
```
sudo apt-get install lm-sensors psensor 
```

then run 
```
sudo sensors-detect
```
answering Yes to all prompts.


Then run 
```
sensors
```
If no output, reboot and try again.

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **sensors**
nouveau-pci-0100
Adapter: PCI adapter
temp1:        +35.0°C  (high = +95.0°C, crit = +105.0°C)

it8720-isa-0228
Adapter: ISA adapter
in0:          +0.99 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.09 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.06 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.25 V  
fan1:        2250 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1147 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +79.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +27.1°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)
```

pic of psensors.

---

### Post by NNJRob on 2013-03-22
Thanks, stinkeye!! 
It works like a charm!

---

### Post by stinkeye on 2013-03-22
> **NNJRob said:**
> Thanks, stinkeye!! 
It works like a charm!
No problem.
It can be hard to tell which reading is your cpu temp.
Just check your cpu temp in your BIOS and use the one that matches.
Opening something like firefox and system monitor together, should see the temp go up 5-6 degrees.

---

### Post by NNJRob on 2013-03-22
Thanks again! 
and I added the link in your 1st reply, to my "lunux links" sheet, in dropbox ;)

Marking this a solved.

---

### Post by jeanfi on 2013-03-23
> **stinkeye said:**
> No problem.
It can be hard to tell which reading is your cpu temp.
Usually, it is not so hard:
[http://wpitchoune.net/psensor/doc/faq.html#S_WhatIsTheSensor](http://wpitchoune.net/psensor/doc/faq.html#S_WhatIsTheSensor)

---

