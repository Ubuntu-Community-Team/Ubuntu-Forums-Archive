---
title: "lm-sensors, is it safe?"
date: 2013-12-18
forum: Hardware
---

### Post by crazymonkey05 on 2013-12-18
i want to update lm-sensors so that i can monitor my pc temp. but i´m scared that it could mess up my system. when probing the areas can it do damage to that area or is it just to the ubuntu install? because i´m fine with it damaging the install but not the MOBO. so any info would be great.

---

### Post by sammiev on 2013-12-18
> **crazymonkey05 said:**
> i want to update lm-sensors so that i can monitor my pc temp. but i´m scared that it could mess up my system. when probing the areas can it do damage to that area or is it just to the ubuntu install? because i´m fine with it damaging the install but not the MOBO. so any info would be great.

You will not damage the motherboard by updating lm-sensors nor the install.

---

### Post by crazymonkey05 on 2013-12-19
Let me rephrase that. I want to detect the sensors. But it warns me that it could cause damage

---

### Post by VMC on 2013-12-19
I'm not sure where your seeing the warning. I've used *lm-sensors* for years without any issues on at least two motherboards.

---

### Post by CharlesA on 2013-12-19
> **crazymonkey05 said:**
> Let me rephrase that. I want to detect the sensors. But it warns me that it could cause damage

> **VMC said:**
> I'm not sure where your seeing the warning. I've used *lm-sensors* for years without any issues on at least two motherboards.

The warning appears when you run sensors-detect.

Just keep hitting enter to the default answers and you will be fine.

---

### Post by VMC on 2013-12-19
> **CharlesA said:**
> The warning appears when you run sensors-detect.

Just keep hitting enter to the default answers and you will be fine.
I just I've always ignored those warnings. Is anyone reported motherboard issues ?

---

### Post by CharlesA on 2013-12-19
> **VMC said:**
> I just I've always ignored those warnings. Is anyone reported motherboard issues ?

I haven't seen anything. I'm guessing it's mostly a "we aren't responsible for any damages" type of message.

---

### Post by VMC on 2013-12-19
I'm missing something here:

```
$** sudo apt-get install lm-sensors**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 213 not upgraded.
Need to get 89.0 kB of archives.
After this operation, 429 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe lm-sensors amd64 1:3.3.3-1ubuntu1 [89.0 kB]
Fetched 89.0 kB in 0s (117 kB/s)    
Selecting previously unselected package lm-sensors.
(Reading database ... 137308 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a3.3.3-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up lm-sensors (1:3.3.3-1ubuntu1) ...
Processing triggers for ureadahead ...
$ **sensors**
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +22.2°C  (high = +70.0°C)
```

Do the warnings come later or for a particular motherboard with multiple sensors?

---

### Post by CharlesA on 2013-12-19
Did you already run sudo sensors-detect?

Mine shows this:

```
charles@Thor:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +48.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +41.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +35.0°C  (high = +80.0°C, crit = +98.0°C)

```

---

### Post by Mark Phelps on 2013-12-19
You have to run "sudo sensors-detect" before you run "sensors".

---

### Post by VMC on 2013-12-19
> **CharlesA said:**
> Did you already run sudo sensors-detect?

Mine shows this:

```
charles@Thor:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +48.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +41.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +35.0°C  (high = +80.0°C, crit = +98.0°C)

```
Thanks.

---

### Post by crazymonkey05 on 2013-12-19
About my OP im sorry for the confusion yes i met sensors-detect. i worried about it damaging some of the super I/O peripherals or other components
here is the part that panics me. ```
ricky@ricky-945G-M3:~$ sensors-detect
You need to be root to run this script.
ricky@ricky-945G-M3:~$ sudo sensors-detect
[sudo] password for ricky: 
# sensors-detect revision 6085 (2012-10-30 18:18:45 +0100)
# System: Gateway 945G-M3 [3.1]
# Board: ELITEGROUP 945GCT-M3


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. [COLOR=#ff0000]This is usually safe.[/COLOR]
Do you want to scan for Super I/O sensors? (YES/no): 


``` this is what worries me (the warning in red) i was doing some research about it and some people have reported that lm-sensors, when probing can confuse some devices and cause them to malfunction or read incorrectly. like some of the people on this thread [http://phoronix.com/forums/showthread.php?84866-LM-Sensors-Sensor-Detect-Is-Causing-Hardware-Issues](http://phoronix.com/forums/showthread.php?84866-LM-Sensors-Sensor-Detect-Is-Causing-Hardware-Issues) , i tried to find resaults if it has caused problems on the ECS 945GCT-M3 motherboard, but no luck same with the search for intel 945g express chipset family, still no one reports a sucess or a failure or damage

---

### Post by grahammechanical on 2013-12-19
Why not install psensor. It puts an icon in the top panel that has a drop down menu that shows fan speeds CPU and motherboard temperature as well as GPU temperature. Depending of course if the motherboard has sensors of those things.

It does not seem to do that intense probing that sensors-detect does. And I have run that command and seen the scary warnings but nothing bad happened.

Regards.

---

### Post by CharlesA on 2013-12-19
Default is YES, so go for it.

---

### Post by crazymonkey05 on 2013-12-21
> **grahammechanical said:**
> Why not install psensor. It puts an icon in the top panel that has a drop down menu that shows fan speeds CPU and motherboard temperature as well as GPU temperature. Depending of course if the motherboard has sensors of those things.

It does not seem to do that intense probing that sensors-detect does. And I have run that command and seen the scary warnings but nothing bad happened.

Regards.

i installed psensors and it read the same values as lm-sensors so its ok. i ran sensors-detect and was not able to find a sensor which is weird because my BIOS can see a system temp. a CPU temp. along with its volteges and all the fans i have installed

---

### Post by CharlesA on 2013-12-21
What CPU and mobo do you have?

---

