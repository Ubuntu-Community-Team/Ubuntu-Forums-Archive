---
title: "lm-sensors data meaning?"
date: 2011-02-02
forum: Hardware
---

### Post by hyfanious on 2011-02-02
Hi i used lm-sensors for monitoring my wind u100 msi in ubuntu
I get these results, but i cann't understand the meaning of them,(each one relate to what part)

acpitz-virtual-0
Adapter: Virtual device
temp1: +48.0°C (crit = +100.0°C) 

coretemp-isa-0000
Adapter: ISA adapter
Core 0: +34.0°C (crit = +90.0°C)

which one is more correct??

---

### Post by hyfanious on 2011-02-03
bump

---

### Post by fjgaude on 2011-02-03
Did you run sensors-detect to see what was available?

Seems both your items are value. The latter is for the CPU core temp.

---

### Post by hyfanious on 2011-02-03
> **fjgaude said:**
> Did you run sensors-detect to see what was available?

Seems both your items are value. The latter is for the CPU core temp.

here is the results:
```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: MICRO-STAR INTERNATIONAL CO., LTD U90/U100

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                Success!
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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
Module i2c-i801 loaded successfully.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
Module i2c-dev loaded successfully.

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): 

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus I801 adapter at d000 (i2c-2)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

Unloading i2c-dev... OK
Unloading i2c-i801... OK


```

so what is first one supposed to mean?

---

### Post by fjgaude on 2011-02-03
It's hard to say... likely some support for the Atom CPU, like a south bridge or PCH (platform controller hub).

I have an Atom mini10n and its cores run at 37C. The other sensor shows as the hard drive. So yours could be showing too.

---

### Post by dabl on 2011-02-03
According to this: [http://www.linuxquestions.org/questions/linux-hardware-18/lm-sensors-acpitz-virtual-0-adapter-virtual-device-temp1-what-is-it-749701/](http://www.linuxquestions.org/questions/linux-hardware-18/lm-sensors-acpitz-virtual-0-adapter-virtual-device-temp1-what-is-it-749701/)

"acpitz-virtual-0" is probably a sensor diode either in the CPU socket, or nearby on the motherboard.

---

### Post by hyfanious on 2011-02-03
> **dabl said:**
> According to this: [http://www.linuxquestions.org/questions/linux-hardware-18/lm-sensors-acpitz-virtual-0-adapter-virtual-device-temp1-what-is-it-749701/](http://www.linuxquestions.org/questions/linux-hardware-18/lm-sensors-acpitz-virtual-0-adapter-virtual-device-temp1-what-is-it-749701/)

"acpitz-virtual-0" is probably a sensor diode either in the CPU socket, or nearby on the motherboard.

so which one is correct?
which one of these numbers shows my cpu temperature correctly?

---

### Post by dabl on 2011-02-06
> **hyfanious said:**
> so which one is correct?
which one of these numbers shows my cpu temperature correctly?

_coretemp_ is the CPU core temperature.

---

### Post by cchhrriiss121212 on 2011-02-06
If you would like a system info that is readable by humans, try inxi:
[http://code.google.com/p/inxi/](http://code.google.com/p/inxi/)
It will figure out what sensor is belongs to what hardware, and shows other useful things too. It should be standard on all distros if you ask me.

---

### Post by dabl on 2011-02-06
> **cchhrriiss121212 said:**
> If you would like a system info that is readable by humans, try inxi:
[http://code.google.com/p/inxi/](http://code.google.com/p/inxi/)
It will figure out what sensor is belongs to what hardware, and shows other useful things too. It should be standard on all distros if you ask me.

Nice!  Thanks for that!  ):P

---

