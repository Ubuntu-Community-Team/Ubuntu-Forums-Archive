---
title: "Fan and system monitoring on Trinity platform"
date: 2013-02-14
forum: Hardware
---

### Post by arieunier on 2013-02-14
Hi there,
I recently bought some new hardware to build a server. It's based on the Trinity platform, from AMD.
My mainboard is an MSI FM2 A85XA G65, with an A10 5800K.
Everything works great.

But i'd like to be able to monitor the system resources, especially  FANs (to adapt their speed depending on the load), temperatures, etc .. 
I've tried several software or applications, but i've never been able to gather the right information and display them, though of course, everything is fully accessible in the bios (can see temperatures, fan speed, ..)

Is there a way to do it ?

---

### Post by tgalati4 on 2013-02-14
What is displayed with:

```
sensors
```

There are a few things to try:

```
sudo modprobe i8k
sensors
```

If i8k loads, then you may see fan speeds.

*fancontrol*, *thinkfan* come to mind, but they require that the fan speeds be seen by *sensors*.

Nagios and Cacti for graphing, monitoring, messaging.

I'm guessing that none of these will work.  In that case send an email to AMD.  We need a laugh today.

Does the BIOS have modes for controlling fan speed?  Does it sound like an airplane taking off?

---

### Post by arieunier on 2013-02-14
I was able to make it work, seems i did not accept all sensors-detect questions ..

I'm able to retrieve the sensors data :
koko@DATA:~$ sensors
f71889a-isa-0600
Adapter: ISA adapter
+3.3V:        +3.30 V  
in1:          +0.93 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.94 V  
in4:          +1.10 V  
in5:          +1.22 V  
in6:          +1.23 V  
3VSB:         +3.31 V  
Vbat:         +3.30 V  
fan1:         901 RPM
fan2:         767 RPM
fan3:         818 RPM
temp1:        +29.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = thermistor
temp2:        +36.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +95.0°C, hyst = +91.0°C)  sensor = thermistor
temp3:        +26.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor



But not to use define threshold or configure fancontrol.
All the test it launches do not have any effect on the fan speed.... Hopefully the bios does give opportunity to let him manage fan speed, so i was able to reduce a bit the noise, but it's not perfect yet :/

---

### Post by damokos on 2013-05-22
> **tgalati4 said:**
> What is displayed with:

```
sensors
```

There are a few things to try:

```
sudo modprobe i8k
sensors
```

If i8k loads, then you may see fan speeds.

*fancontrol*, *thinkfan* come to mind, but they require that the fan speeds be seen by *sensors*.

Nagios and Cacti for graphing, monitoring, messaging.

I'm guessing that none of these will work.  In that case send an email to AMD.  We need a laugh today.

Does the BIOS have modes for controlling fan speed?  Does it sound like an airplane taking off?

Hi All,

I try to become som informations about the temperatur and the fans on my desktop, but isn't work.
I have an A10 5800K and Asrock FM2 A75 Pro4-M so I try sensors command and become the following:
```

root@octopus:~# sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)

```
The temp is starting about 10 °C but give each time 2 °C less so after 5 executing it's only 0.
I can't have anyting about the fans and voltage.

Have you an idea how can I configure the lm-sensors well and use it?

---

