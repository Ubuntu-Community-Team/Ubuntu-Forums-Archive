---
title: "problem with lm-sensors and temperature"
date: 2011-03-03
forum: Hardware
---

### Post by danne on 2011-03-03
Hi!
When I run "sensors" in the terminal, I get the following message:

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Also, I have the feeling my laptop needs to get too hot before the fan starts spinning..

any suggestions?

(cpu = i3 m330 in an acer aspire 5741g 64-bit..Ubuntu 10.10)

---

### Post by danne on 2011-03-03
sorry..
[http://ubuntuforums.org/showthread.php?t=1643069&highlight=fan+speed+control](http://ubuntuforums.org/showthread.php?t=1643069&highlight=fan+speed+control)

already posted 

but no solution.. :)

---

### Post by Call_M on 2011-03-04
I have a similar problem. I want a better read of my CPU and MB temperature. This to control my fans. At the moment I use the fan control in my BIOS but this is limited and therefore my pc is buzzing even when i´m logged off. And this sucks big time.

I found that the problems occur because linux does not support all sensors. So for a lot of sensors no drivers are available. 

I find 1 sensor when I run the following command in a terminal ```
sensors
```The output is for me:

> k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +15.5°C  (high = +70.0°C)Which is probably the temperature of my sound card. Which I really do not care about. So to get a better read on which sensors are available I typed the following command: 

```
sudo sensors-detect
```Just type a few times yes to proceed.

My summary looks as follows:

> Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton W83677HG-I Super IO Sensors' (confidence: 9)

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Note: there is no driver for Nuvoton W83677HG-I Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OKSo it seems I have to wait until the drivers are written. Until then I give my CPU and MB an overdose of wind, and work behind my PC with earplugs in.

Or does somebody have a better idea??

---

