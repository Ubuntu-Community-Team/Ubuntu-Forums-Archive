---
title: "Tweaking lm-sensors?"
date: 2017-05-21
forum: Hardware
---

### Post by eezacque on 2017-05-21
Currently, my output of 'sensors' is minimal on my Asus Z97-Pro:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +105.0°C)
temp2:        +29.8°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +28.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:         +28.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:         +26.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:         +26.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:         +25.0°C  (high = +80.0°C, crit = +100.0°C)

asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM



I am happy with the temperature readings, just would like to have access to fan readings.

Is there any chance of tweaking lm-sensors to give access to more sensor readings?

---

### Post by Yellow Pasque on 2017-05-21
Try:
```
sudo modprobe -v nct6775
sensors
```

If that works, you can put nct6775 in /etc/modules, or you can run 'sudo sensors-detect' and let it do that for you.

---

### Post by eezacque on 2017-05-21
> **Temüjin said:**
> Try:
```
sudo modprobe -v nct6775
sensors
```

If that works, you can put nct6775 in /etc/modules, or you can run 'sudo sensors-detect' and let it do that for you.

Been there, done that, doesn't work...

---

### Post by Yellow Pasque on 2017-05-21
Any suggestions herehelpful? [https://web.archive.org/web/20150512184331/http://lists.lm-sensors.org:80/pipermail/lm-sensors/2014-November/042908.html](https://web.archive.org/web/20150512184331/http://lists.lm-sensors.org:80/pipermail/lm-sensors/2014-November/042908.html)

---

### Post by eezacque on 2017-05-22
> **Temüjin said:**
> Any suggestions herehelpful? [https://web.archive.org/web/20150512184331/http://lists.lm-sensors.org:80/pipermail/lm-sensors/2014-November/042908.html](https://web.archive.org/web/20150512184331/http://lists.lm-sensors.org:80/pipermail/lm-sensors/2014-November/042908.html)

Yes! Setting the acpi_enforce_resources=lax boot parameter did the job.

Thanks!

---

