---
title: "trying to find out gpu temperatures"
date: 2018-04-27
forum: Hardware
---

### Post by cheesecake420 on 2018-04-27
after installing sensors, then running sensors-detect (saying yes to everything) and then sensors, i get this output

```
coretemp-isa-0000
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +29.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:        +28.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:        +29.0°C  (high = +84.0°C, crit = +100.0°C)

acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)

pch_skylake-virtual-0
temp1:        +31°C



```

now i don't think my gpu is 30 degrees, and if it is, which one is it?
using gt 1030; pentium g4400; ubuntu 16.04

---

### Post by sevendogsbsd on 2018-04-27
Assuming by "gt1030" you are using an Nvidia card? If so, I pull my gpu temp using "nvidia-settings" in conky. Not sure how to do it with sensors, maybe someone else can chime in. Right now, my gpu is running at 29c, idling.

---

### Post by Bashing-om on 2018-04-27
cheesecake420; Hello;

I track system temps :
```

inxi -F

```
will require installing the tool.
```

sudo apt install inxi

```
And take the time to read the manual :)
```

man inxi

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2018-04-27
Here is a script i use 
```
#!/bin/sh
if [ ! -e /dev/nvidiactl ];then
    sensors | grep -A2 nouveau | tail -1 | awk '{print $2}' | sed 's/+//'
    exit
fi
out="$(nvidia-smi -q -d TEMPERATURE)"
temp=$(echo "$out" | grep 'Gpu' | awk '{print $3}') # Works on my old GeForce 8200M (304 driver)
if [ -z "$temp" ];then
    temp=$(echo "$out" | grep 'GPU Current' | awk '{print $5}') # Works on my GTX 650 TI Boost (390 driver)
fi
echo "$temp°C"

```
Supports the nouveau driver the old 304 driver and the current 390 driver

I was not aware of inxi

---

### Post by Yellow Pasque on 2018-04-28
^That will work. Or, to make it a bit easier, you can run this once:
```
echo alias gputemp="nvidia-smi -q | grep 'GPU Current'" | tee -a ~/.bashrc
```

And now, you can just type gputemp (or whatever you choose to name the command):
```
$ gputemp 
        GPU Current Temp            : 57 C
```

---

### Post by sevendogsbsd on 2018-04-28
I had forgotten about inxi - thanks for the tip Bashing-om.

---

