---
title: "About max CPU temperature"
date: 2014-03-25
forum: Hardware
---

### Post by cogset on 2014-03-25
I've realized that the output of sensors says 
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +35.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +34.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +27.0°C  (high = +82.0°C, crit = +102.0°C)
```

but the manufacturer's spec for my CPU (Intel Core i3-2100 CPU) states that the max case temperature is 69° C [http://ark.intel.com/products/53422/](http://ark.intel.com/products/53422/) .

So,where do those numbers  come from? Is that some random value,or are they read from a different sensor location?

I've never actually pushed my CPU beyond 55-ish,but what will happen if eventually some application will push it further?
Does the system still know when to throttle it down,regardless of the accuracy of those max values in sensors?

On a related matter,my motherboard Asus P8H61-M LE has three different performance profiles and different fan profiles as well,I've never checked if they make actually a difference,but -come to that- does Ubuntu override those BIOS settings or respect them?

---

### Post by tgalati4 on 2014-03-25
Case temperature is a reference for designers to size the heat sink that goes on top of the CPU die case.  So your heat sink needs to wick away enough heat to keep a thermocouple placed between the CPU chip and the heat sink below 69C.  Most CPU's have a thermal diode or thermister inside the die and that temperature needs to stay below a sensiible value--usually below 100C.  Spend some time on an overclocker's forum and you will see what temperatures the i3 can really handle.

Your BIOS should have built-in thermal protection, and you might be able to change the trigger points.  Intel processors also have safety mechanisms such as declocking and CPU halt if the temperature gets too high.

You can change the limits in *sensors*:

```
man sensors
man sensors.conf
```

---

### Post by grahammechanical on 2014-03-25
The case temperature is not the same as the CPU temperature. Your CPU cores are running at +35 and +27 which is much below the +82 which is considered High and very very much below the +102 which is considered Critical. +82 to +102 is not the actual temperature but the range of temperatures that put the CPU at risk of breakdown. What are you worried about?

Case temperatures can increase if the air vents are blocked in some way. If the case temperature rises then the CPU cooling fans and heat sinks will not be effective in keeping the CPU within optimum operating temperatures.

If you want to monitor temperatures then install Psensor. That will put an icon in the top panel and from that icon we get a menu that lists, among other things, CPU Temperature, motherboard temperature, and individual core temperatures, and also the temperature of the graphic adapter. Fan speed are also included. Of course Psenor will only be able to show these things if the hardware sensors are there in the first place.

Oh, one other thing. with Psensor we can set the temperature at which the utility will activate an alarm in the top panel.

Regards.

---

### Post by cogset on 2014-03-27
Thanks for your replies:to sum up,I wasn't actually worried about  something particularly,as I reckon that temperatures usually ranging  below 40° C  and occasionally peaking around 55° C  (during some very  intensive tasks) are probably OK for any processor.
I was simply  curious about the discrepancy of the Intel tech data (69° C) and the output of  sensors,as far as max temperatures go,and to be fair I think I'm still not getting it:when I read 
```
high = +82.0°C, crit = +102.0°C

```
is that some default value that has no special meaning for a given CPU,or is it *actually related* to the actual CPU on my computer?
I understand that I can in theory edit sensors.conf,but the question is,should I ? I mean,it looks kinda complicated and I wouldn't want to mess up with it  unless it's really necessary.

Furthermore,I don't think I can get anything more than the output from the three sensors above (Physical id 0,Core 0,Core 1) 
 as no hardware monitor that I've tried so far in Linux (including Psensor) has ever managed to display fan speeds on this computer (on a side note,back when I had a Windows partition here,the Asus utility could read fan speeds,so probably the sensors are there but lm-sensors can't use them?),so either with Psensor or the standard panel applet (I'm using MATE) I would have the same information,I suppose.

About my original BIOS question,is it possible to understand if the settings for fan speed profile and system overall performance (I think this motherboard has 3 profiles:energy saving,standard and performance) are effective,or the kernel takes over once the system is booted and ignores those settings?
I'm asking because some people claim that those BIOS settings are actually effective only in a Windows system once the the OEM drivers for the motherboard are installed,and are ignored by the Linux kernel.

---

### Post by Yellow Pasque on 2014-03-27
> high = +82.0°C, crit = +102.0°C
If all 3 sensors are giving that exact value, it's probably garbage.

> does Ubuntu override those BIOS settings or respect them? 
The OS will not override the BIOS fan control.

---

### Post by cogset on 2014-03-28
Yes,correct:those values are identical for all three sensors-therefore are useless,as I kinda imagined.

On the BIOS/fan control subject:can we assume that if the OS does not override the BIOS fan control,it won't override the motherboard CPU/performance settings as well,or is this a different matter?

---

