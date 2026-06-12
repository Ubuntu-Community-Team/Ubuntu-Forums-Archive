---
title: "lm-sensors does not show complete sensors"
date: 2014-09-08
forum: Hardware
---

### Post by Frozenic on 2014-09-08
need a little help here guys. I have lm-sensors installed on my ubuntu 14.04, i've run sensor-detect and answer all question with 'yes' and restarted my laptop.
I ran 'sensors' but the output just like this

```
dhemas@1431tu:~/Desktop$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  (crit = +110.0°C)
temp2:         +0.0°C  (crit = +127.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +45.0°C  (high = +72.0°C, crit = +90.0°C)
Core 0:         +45.0°C  (high = +72.0°C, crit = +90.0°C)
Core 1:         +38.0°C  (high = +72.0°C, crit = +90.0°C)

```

other sensors like fan speed and voltage isn't appear. How I can fix this?

and here the output of 'sensor-detect'

```
# sensors-detect revision 6253 (2014-06-26 16:37:22 +0200)
# System: Hewlett-Packard HP 1000 Notebook PC [088F130000005910000600000] (laptop)
# Board: Hewlett-Packard 1854


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               Yes
Found unknown chip with ID 0x8517
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Panther Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.


Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: DPDDC-D (i2c-6)
Do you want to scan it? (YES/no/selectively): yes




Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)


Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): yes
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.


Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

```

my laptop is HP 1000-1431tu
any help will be appreciated and sorry for my bad english

---

### Post by Dennis N on 2014-09-08
It's my experience too that not all the potential readings can be obtained - fan speed, voltage, for example. Either there are no sensors, or they cannot be accessed this way.

---

### Post by Frozenic on 2014-09-09
thanks for your answer
I have try hwinfo program in windows and it can show all sensor in my laptop. But for now and further I want to use ubuntu for my primary OS, and usually I always check my laptop temp, etc :(
anyone can help? please? :(

---

### Post by Yellow Pasque on 2014-09-10
```
Trying family `National Semiconductor/ITE'...               Yes
Found unknown chip with ID 0x8517
```

It looks like an ITE 8517. I don't think that Super I/O chip is supported (yet).
[https://github.com/torvalds/linux/blob/master/drivers/hwmon/it87.c](https://github.com/torvalds/linux/blob/master/drivers/hwmon/it87.c)
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

---

