---
title: "hp dv9000 -- can't manually control fan speed"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by aoeuid on 2007-11-10
I have gutsy on a dv9000, and am trying to figure out a way to conrol fan speed. The fan only starts running quickly when the cpu gets hot, but quite often the HDDs get hot first, which is quite annoying. I tried installing lm-sensors and pwmconfig, but they don't seem to work properly.

I get:
```
$ sudo sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +19°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +20°C  (high =  +100°C)                   

```
and:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

Please tell me if I did anything wrong in installing the two or something. (I followed [this thing]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29"))

---

### Post by ZeldaFan on 2008-06-01
I have the same problem here, and no one seems to know the answer. I know this thread is old, but I was wondering if you ever ended up solving your problem.

---

