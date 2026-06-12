---
title: "HELP with [lm-sensors] and [msi p67a-gd65]"
date: 2011-04-30
forum: Hardware
---

### Post by ppjose on 2011-04-30
hi

msi p67a-gd65 rev b3 sandy bridge
core i5
ubuntu natty 64bit

Why not detect/show voltages, chipset temp etc? help please..

THANKS!!!

> # sensors-detect revision 5861 (2010-09-21 17:21:05 +0200)
# System: MSI MS-7681
# Board: MSI P67A-GD65 (MS-7681)

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
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0x1005
    (logical device 4 has address 0x290, could be sensors)

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
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       Success!
    (confidence 6, driver `lm78')
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-6)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-7)
Do you want to scan it? (YES/no/selectively): 

Next adapter: SMBus I801 adapter at f000 (i2c-8)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Driver `lm78':
  * ISA bus, address 0x290
    Chip `National Semiconductor LM78' (confidence: 6)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
lm78
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

#----lm-sensors----
# Chip drivers
coretemp
lm78
#----lm-sensors----


> coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +32.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +29.0°C  (high = +80.0°C, crit = +98.0°C)

---

