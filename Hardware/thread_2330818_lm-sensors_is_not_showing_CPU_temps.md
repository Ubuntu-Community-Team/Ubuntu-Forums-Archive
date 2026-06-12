---
title: "lm-sensors is not showing CPU temps"
date: 2016-07-15
forum: Hardware
---

### Post by ninja_unmatched on 2016-07-15
Been trying to monitor the temps but lm-sensors is not recognizing the CPU...

```

# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: Supermicro X6DA8 [0123456789]

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
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Winbond W83627HF/F/HG/G Super IO Sensors'            Success!
    (address 0x295, driver `w83627hf')
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
Found `IPMI BMC Unknown'...                                 Success!
    (confidence 8, driver `to-be-written')

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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801EB ICH5
Module i2c-i801 loaded successfully.

Next adapter: nouveau-0000:06:02.0-0 (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: nouveau-0000:06:02.0-1 (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: SMBus I801 adapter at 1100 (i2c-2)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x1f
Probing for `Texas Instruments TMP421'...                   No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `Atmel AT30TS00'...                             No
Client found at address 0x2f
Handled by driver `w83792d' (already loaded), chip type `w83792d'
Client found at address 0x51
Handled by driver `eeprom' (already loaded), chip type `eeprom'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x52
Handled by driver `eeprom' (already loaded), chip type `eeprom'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x53
Handled by driver `eeprom' (already loaded), chip type `eeprom'
    (note: this is probably NOT a sensor chip!)

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `w83792d':
  * Bus `SMBus I801 adapter at 1100'
    Busdriver `i2c_i801', I2C address 0x2f
    Chip `w83792d' (confidence: 6)

Driver `w83627hf':
  * ISA bus, address 0x295
    Chip `Winbond W83627HF/F/HG/G Super IO Sensors' (confidence: 9)

Driver `to-be-written':
  * ISA bus
    Chip `IPMI BMC Unknown' (confidence: 8)

Note: there is no driver for IPMI BMC Unknown yet.
Check http://www.lm-sensors.org/wiki/Devices for updates.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
w83627hf
w83792d
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

```

It is an older server with 2 Intel XEON 3.0Ghz (Pentium 4 class with HT)

---

