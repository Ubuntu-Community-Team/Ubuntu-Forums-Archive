---
title: "Acer, acpi and temperature"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by herlock on 2006-03-08
First, I would like to excuse my very bad english.

I bought my Acer 5024WLMI (amd64) and I've installed Ubuntu Breezy for amd64. My problem is that, according to "acpi -V" the temperature are very high !
And the thing is very very weird is that the temperature are high but i'm not doing anything !!!

for exemple:

```
k# acpi -V
     Thermal 1: ok, 58.0 degrees C
     Thermal 2: ok, 62.0 degrees C
     Thermal 3: ok, 76.0 degrees C
  AC Adapter 1: on-line

``` 
With Windows, I have +- 53°C

I also try a live CD. Kubuntu, but the 32bits version and there is no these high temperature. With a 64bit's live CD, the temperature are also high...

So, is it possible that the acpi with 64bit are not working correctly ? 


Thank you

**EDIT:** When I do a cat /proc/acpi/thermal_zone/*/* the result is:

```
# cat /proc/acpi/thermal_zone/*/*
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             57 C
critical (S5):           102 C
passive:                 82 C: tc1=2 tc2=5 tsp=300 devices=0xffff81001fe99840
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             61 C
critical (S5):           83 C
passive:                 69 C: tc1=2 tc2=5 tsp=300 devices=0xffff81001fe99840
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             72 C
critical (S5):           115 C
passive:                 82 C: tc1=2 tc2=5 tsp=300 devices=0xffff81001fe99840

```

Does it mean that there is no danger because I can go until 115°C ?

---

### Post by Heliix on 2006-03-08
hi
just now, i don't know how to set these parameters mut try browsing the acpi documentation

the temperatures you mention are terrible, i had the same problem on Omnibook and maybe it contributed to my hdd failure last week (perhaps i've "boiled" it).. 

to turn the fan on:
echo on > /proc/acpi/fan/FAN/state
(as root)

to turn the fan off-or, to the automatic mode again:
echo 3 > /proc/acpi/fan/FAN/state

i'll follow this thread as i also wonder how to set the temperature limits..

---

