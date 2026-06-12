---
title: "Lenovo w520 Fan Issue"
date: 2012-04-30
forum: Hardware
---

### Post by cbennett926 on 2012-04-30
Hello,

I hate to post so much on here, but the fans on my laptop won't engage in heavy loads. They do run and keep the laptop cool (40 degrees idle temp), however the fans do not change RPM when the load is heavier. Does anyone know any scripts or anything?

---

### Post by cbennett926 on 2012-06-14
Bump

---

### Post by Redblade20XX on 2012-06-15
Check your BIOS for fan configuration settings. These are usually under the advance settings. From what other people have said, there is a bug in the kernel which keeps your processor fully clocked which drives up heat.

-Red

---

### Post by cbennett926 on 2012-07-11
> **Redblade20XX said:**
> Check your BIOS for fan configuration settings. These are usually under the advance settings. From what other people have said, there is a bug in the kernel which keeps your processor fully clocked which drives up heat.

-Red

Hey, didn't know if anyone has any other thoughts on this? I checked the bios and they are set normal. On this system when the CPU is kept fully clocked the fans kick up RPM by a lot, and they aren't doing this.

---

### Post by Redblade20XX on 2012-07-11
> **cbennett926 said:**
> Hey, didn't know if anyone has any other thoughts on this? I checked the bios and they are set normal. On this system when the CPU is kept fully clocked the fans kick up RPM by a lot, and they aren't doing this.

Have you tried lm-sensors and have gotten temperature readings?
```
sudo apt-get install lm-sensors
``````
sudo sensors-detect
``````
sensors
```Post the output of sensors.

Do you have the latest BIOS?

You can also try isolating the OS from the BIOS by pushing either:
```
acpi.power_nocheck=1
```or
```
acpi_osi=linux 
```through grub to see if it does anything.

- Red

---

### Post by cbennett926 on 2012-07-12
> **Redblade20XX said:**
> 

```
sensors
```Post the output of sensors.

Do you have the latest BIOS?

- Red


```


acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +99.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        1985 RPM


```

See, it idles just fine, but when I do something more intense, the fan will only go up to about 3200 RPM, and the temp will go up to about 85C, and that's from playing a game (MineCraft to be specific).  I know the fan can go faster because on Windows, when it switches to discrete, (which is what it is always on on Linux) the fan kicks in to overdrive.

---

### Post by Redblade20XX on 2012-07-13
> **cbennett926 said:**
> ```


acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +99.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        1985 RPM


```See, it idles just fine, but when I do something more intense, the fan will only go up to about 3200 RPM, and the temp will go up to about 85C, and that's from playing a game (MineCraft to be specific).  I know the fan can go faster because on Windows, when it switches to discrete, (which is what it is always on on Linux) the fan kicks in to overdrive.

After digging around a bit, maybe this will help...
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

- Red

---

