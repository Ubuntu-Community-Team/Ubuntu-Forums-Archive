---
title: "Unable to load it87 module"
date: 2019-09-30
forum: Hardware
---

### Post by spookybathtub on 2019-09-30
I have a server running Ubuntu 16.04 on Asus AT3IONT-I Deluxe.  It's been running for years and I rarely reboot so I don't know when this issue first started.  But today I noticed a warning during reboot that **systemd-modules-load.service** failed to load.  This is happening because of the it87 module, which was inserted to /etc/modules by sensors-detect.
I am getting several sensors from the atk0110 driver as shown below, so maybe it87 is no longer necessary?  I could just remove it87 and call it a day, but I'm curious why sensors-detect still thinks this is necessary.

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +78.0°C  (crit = +125.0°C)
Core 1:       +78.0°C  (crit = +125.0°C)


atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.13 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.31 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.07 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.34 V  (min = +10.20 V, max = +13.80 V)
POWER FAN Speed:      0 RPM  (min =  600 RPM, max = 7200 RPM)
CPU FAN Speed:        0 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS FAN Speed:  636 RPM  (min =  600 RPM, max = 7200 RPM)
CPU Temperature:    +53.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +39.0°C  (high = +45.0°C, crit = +95.0°C)
```

I just re-ran sensors-detect again and it still thinks I need it87:
```
# sensors-detect# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)
# Board: ASUSTeK Computer INC. AT3IONT-I DELUXE
# Kernel: 3.13.0-106-generic x86_64
# Processor: Intel(R) Atom(TM) CPU 330 @ 1.60GHz (6/28/2)


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
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8721F/IT8758E Super IO Sensors'                Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-nforce2' for device 0000:00:03.2: nVidia Corporation nForce SMBus (MCP79)
Module i2c-dev loaded successfully.


Next adapter: SMBus nForce2 adapter at 4e00 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)


Next adapter: NVIDIA i2c adapter 0 at 3:00.0 (i2c-1)
Do you want to scan it? (yes/NO/selectively): 


Next adapter: NVIDIA i2c adapter 2 at 3:00.0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): 


Next adapter: NVIDIA i2c adapter 3 at 3:00.0 (i2c-3)
Do you want to scan it? (yes/NO/selectively): 




Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8721F/IT8758E Super IO Sensors' (confidence: 9)


Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)


To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!


Do you want to add these lines automatically to /etc/modules? (yes/NO)n


Unloading i2c-dev... OK
Unloading cpuid... OK


# modprobe it87
modprobe: ERROR: could not insert 'it87': Device or resource busy
```

---

### Post by Yellow Pasque on 2019-09-30
[https://www.linuxquestions.org/questions/slackware-14/module-it87-ko-won%27t-load-4175608152/](https://www.linuxquestions.org/questions/slackware-14/module-it87-ko-won%27t-load-4175608152/)

TL;DR: You don't need it87 if you use the asus module.

---

