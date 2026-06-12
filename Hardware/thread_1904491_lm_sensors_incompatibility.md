---
title: "lm_sensors incompatibility?"
date: 2012-01-04
forum: Hardware
---

### Post by Drak3 on 2012-01-04
So, I recently changed my home server over to Intel from AMD, and I have been unable to get lm_sensors to report anything.  specifically, I'm looking for the CPU temps

My question is, does anyone know if there is anything I can do to get lm_sensors to pick up the temps?  I had to load a module (i think) to get the temps from by AMD CPU, but i'm finding nothing on google.

for reference, i have an i7 2600 with an ASRock Extreme3 Rev3 mobo.  (i know lm sensors is at least partially motherboard dependent)

again, any help anyone could give me would be asweome

---

### Post by dFlyer on 2012-01-04
depending on what version of ubuntu your running have you installed lm-sensors? On my 11.10 I had to install it, with sudo apt-get install lm-sensors.

---

### Post by Drak3 on 2012-01-04
its 10.04 LTS with lm sensors 3.1.2.  i tried manually downloading the newest version, but that still did not help

---

### Post by whatthefunk on 2012-01-04
Did you do 
```
sudo sensors-detect
```
??

---

### Post by Drak3 on 2012-01-04
> **whatthefunk said:**
> Did you do 
```
sudo sensors-detect
```
??

yes, i did.  i get the same result below each time.

```
drake@unimatrix434:~$ sudo sensors-detect 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: To Be Filled By O.E.M. To Be Filled By O.E.M.
# Board: ASRock Z68 Extreme3 Gen3

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc333
    (logical device B has address 0x290, could be sensors)
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
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

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
Found unknown SMBus adapter 8086:1c22 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Next adapter: nouveau-0000:01:00.0-0 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: nouveau-0000:01:00.0-1 (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

---

