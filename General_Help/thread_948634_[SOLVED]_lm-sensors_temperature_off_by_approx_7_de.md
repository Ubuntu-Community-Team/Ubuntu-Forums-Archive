---
title: "[SOLVED] lm-sensors temperature off by approx 7 degress"
date: 2008-10-15
forum: General Help
---

### Post by akudewan on 2008-10-15
Hi,

My bios reports a CPU temperature approximately 7 degrees higher than what is reported by lm-sensors. Is there any way I can add an offset to the temperature reported in linux?

I tried running sensors-detect again, and added the lines to /etc/modules, but it remained the same

I have a Core2Duo E6550, on a NVidia nForce 630i chipset.

---

### Post by Yellow Pasque on 2008-10-15
It's possible that lm-sensors is reading a different sensor (for example, the CPU often has its own sensor in addition to the one on the sensor chip). Also, once you boot into the OS, the CPU will probably undervolt/underclock and cool off.

What is the output of sensors?
```
sensors
```

---

### Post by akudewan on 2008-10-15
Thanks for the reply. Here's the output of Sensors:
```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (crit = +85.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (crit = +85.0°C)


```

The room temperature right now is also 30°C. IMO, the CPU temperature should be at least a few degrees higher. So what the BIOS is reporting may be more reliable ?

Edit:
/etc/modules contains these:
```

# Chip drivers
it87
coretemp

```

---

### Post by Yellow Pasque on 2008-10-15
The output from the coretemp sensors is from the CPU's internal sensor. It appears your BIOS reads from the motherboard's temperature sensor. For some reason, the output from your it87 motherboard sensor is not showing. It should look like this:
```
it8718-isa-0e80
Adapter: ISA adapter
in0:         +1.09 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.14 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.23 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +2.21 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +1.18 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.82 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.33 V
fan1:          0 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +68.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp3:       +24.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +1.550 V
```

Try to load the module manually and then get output:
```
sudo modprobe it87
sensors
```

---

### Post by akudewan on 2008-10-16
Hi,

I tried out your suggestion, but the output of sensors is still the same

```

akudewan@ranjandesk:~$ sudo modprobe it87
[sudo] password for akudewan:

akudewan@ranjandesk:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +28.0°C  (crit = +85.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +28.0°C  (crit = +85.0°C)

```

:confused:

---

### Post by llebegue on 2008-10-16
Try to post on lm-sensors mailing list. It's very active and the guys overthere are the most knowledged I know about sensors.

See the page [http://lists.lm-sensors.org/mailman/listinfo/lm-sensors](http://lists.lm-sensors.org/mailman/listinfo/lm-sensors)

---

### Post by akudewan on 2008-10-19
> **llebegue said:**
> Try to post on lm-sensors mailing list. It's very active and the guys overthere are the most knowledged I know about sensors.

See the page [http://lists.lm-sensors.org/mailman/listinfo/lm-sensors](http://lists.lm-sensors.org/mailman/listinfo/lm-sensors)

Thanks, I'll do that. If I find a solution, I'll post it here as well.

---

### Post by akudewan on 2008-10-26
I found that the Gnome sensors-applet allows me to add a temperature offset. I'm using this, so I'm satisfied for the time being.

Also, I found the 'proper' way of doing it: [http://www.lm-sensors.org/wiki/FAQ/Chapter3#MyBIOSreportsamuchhigherCPUtemperaturethanyourmodules](http://www.lm-sensors.org/wiki/FAQ/Chapter3#MyBIOSreportsamuchhigherCPUtemperaturethanyourmodules)

---

