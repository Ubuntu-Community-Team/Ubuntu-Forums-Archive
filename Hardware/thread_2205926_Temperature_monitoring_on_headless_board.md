---
title: "Temperature monitoring on headless board"
date: 2014-02-16
forum: Hardware
---

### Post by IanVaughan on 2014-02-16
Whats the best way to setup and run temperature monitoring?

I have a AMD CPU, and a ASUSTeK (M4A88T-M) mobo.

---

### Post by tgalati4 on 2014-02-16
Do you have lm-sensors installed?

```
apt-cache policy lm-sensors
```

If so, then what is the output of:

```
sensors
```

It might look like:

tgalati4@Mint14-Extensa ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +36.0°C  (crit = +95.0°C)
temp2:        +36.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +28.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +34.0°C  (high = +100.0°C, crit = +100.0°C)

Check your BIOS for temperature monitoring.  For a headless server, having beep codes is helpful for overtemperature conditions.  If the server is buried underground or in a barn or attic, then you would set up *nagios* or *psensor* and monitor it remotely and *sensord* for logging.

---

### Post by IanVaughan on 2014-02-16
Excellent, I did not have sensors installed, so added that, and get a nice load of info back!

```

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.04 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.34 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +11.97 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1318 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS FAN Speed:    0 RPM  (min =  600 RPM, max = 7200 RPM)
POWER FAN Speed:      0 RPM  (min =  600 RPM, max = 7200 RPM)
CPU Temperature:    +29.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +34.0°C  (high = +45.0°C, crit = +75.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +19.2°C  (high = +70.0°C)
                       (crit = +99.5°C, hyst = +97.5°C)


```

I guess then the best thing to do is script/cron piping that into a file, and then parse that to get stats?

Many thanks!

---

### Post by tgalati4 on 2014-02-17
I believe *sensord* dumps the data to the /var/log/syslog as part of routine datalogging.  There may be other sensor monitoring tools that don't require you to write a script.  But you will have to search for them.  I know that the gnome panel applet had warning levels that you could set for each sensor.  For a headless server you would want an email or text message when things are grossly out-of-bounds.

```
man sensors.conf
```

You can set limits in /etc/sensors3.conf even beep codes when things go bad.

---

