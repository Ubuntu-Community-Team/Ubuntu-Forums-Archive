---
title: "Fan Issues: lm-sensors does not output fan RPM"
date: 2015-11-02
forum: Hardware
---

### Post by nina5 on 2015-11-02
Since installing ubuntu, my fan has not been running at all. I have an Asus X200MA laptop.

I installed lm-sensors and ran sensors-detect (See below).

```
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: ASUSTeK COMPUTER INC. X200MA [1.0] (laptop)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Found unknown SMBus adapter 8086:0f12 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.
```

when I run sensors after updating /etc/modules I do not see any information about fan RPM, I just see a few temperatures (last one is really high).

```
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +75.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +49.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +50.0°C  (high = +105.0°C, crit = +105.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:       +6280.0°C 

```

I also installed fancontrol and ran pwmconfig:

```
# pwmconfig revision 6166 (2013-05-01)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no fan-capable sensor modules installed


```

I'm not sure if I'm missing a driver or something that is causing lm-sensors to not detect my fan. I noticed it did not detect a super I/O chip and I have not been able to find any information about that for my laptop either. Not sure where to go from here...for now I'm just avoiding running long, computationally intensive programs to avoid overheating.

Any help with this would be really appreciated.

Thanks!

---

