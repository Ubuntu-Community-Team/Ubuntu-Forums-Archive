---
title: "lm-sensors on ECS GeForce6100PM-M2 V2.0"
date: 2016-01-26
forum: Hardware
---

### Post by jrollf on 2016-01-26
I have been going around in circles trying to get lm-sensors to work on my computer (specs in signature) that has an ECS GeForce6100PM-M2 V2.0 motherboard.  For some reason lm-sensors only finds ONE sensor (labled temp1) on my entire motherboard and says I have a IT87 chip.  I believe it is the cpu socket temperature as the speed of the CPU fan seems to follow the change in temp of this sensor and the 'crit' temp matches the setting in BIOS and changed along with it.  

I've done extensive 'Googling' and have found posts talking about getting the labels and voltage adjustments right for this motherboard but none on how they got the sensors to work in the first place.  I followed these instructions: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Any suggestions would be great, below are the outputs of the various steps and the contents of config files, what am I missing? :confused::

Output of 'sensors'
```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +70.0°C)

```

Output of 'sensors-detect':
```

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no):
Module cpuid loaded successfully.
watching /run/udev failed
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
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8726F Super IO Sensors'                        Success!
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
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-nforce2' for device 0000:00:01.1: nVidia Corporation nForce SMBus (MCP61)

watching /run/udev failed
Next adapter: SMBus nForce2 adapter at 1c00 (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes
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

Next adapter: SMBus nForce2 adapter at f400 (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: nouveau-0000:00:0d.0-0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: nouveau-0000:00:0d.0-1 (i2c-3)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: nouveau-0000:00:0d.0-2 (i2c-4)
Do you want to scan it? (yes/NO/selectively): yes

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8726F Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

```

Contents of /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc

# Generated by sensors-detect on Tue Jan 19 16:23:20 2016
# Chip drivers
it87

```

I have not modified sensors3.conf

I've also noticed that the lm-sensors.org website has been down for a while now, is this a dead project?  Should I use something different?

---

