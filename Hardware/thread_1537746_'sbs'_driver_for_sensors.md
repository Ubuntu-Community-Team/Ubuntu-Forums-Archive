---
title: "'sbs' driver for sensors"
date: 2010-07-24
forum: Hardware
---

### Post by cci[RR]us on 2010-07-24
Hi,

I need some help in getting sensors working. Below is the output from sensors-detect (see bold for the key result):
```
$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: FUJITSU LifeBook S Series (laptop)
# Board: FUJITSU FJNB182

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
Trying family `SMSC'...                                     Yes
Found unknown non-standard chip with ID 0x7a
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801DB ICH4
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: intel drm DVODDC_D (i2c-2)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: intel drm DVOI2C_E (i2c-3)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: SMBus I801 adapter at 1ca0 (i2c-4)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x0b
Probing for `Smart Battery'...                              Success!
    (confidence 5, driver `sbs')
Client found at address 0x19
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95231'...             No
Probing for `National Semiconductor LM95241'...             No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

[b]Driver `sbs':
  * Bus `SMBus I801 adapter at 1ca0'
    Busdriver `i2c_i801', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Warning: the required module sbs is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check http://www.lm-sensors.org/wiki/Devices for
driver availability.

No modules to load, skipping modules configuration.[/b]

Unloading i2c-dev... OK
Unloading i2c-i801... OK
```
Is the module 'sbs' available on my Lucid 2.6.32-23-generic? How do I get the module 'sbs' installed?

Thank you!

---

### Post by cci[RR]us on 2010-07-25
Does anyone know how do get 'sbs' driver installed?

---

### Post by Lamukra on 2011-08-31
I am getting this instead of SMBus

```
[SIZE="2"]Driver `sbs':
  * Bus `Radeon i2c bit bus 0x93'
    Busdriver `UNKNOWN', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Warning: the required module sbs is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check http://www.lm-sensors.org/wiki/Devices for
driver availability.[/SIZE]
```

Looking for it, still...

---

### Post by .... on 2011-08-31
In Natty, the SBS code is built into the kernel, and not a separate module, so this is okay. If the radeon temp sensor is supported in the kernel, then sensors should show its output. Mine looks like:
```
radeon-pci-0100
Adapter: PCI adapter
temp1:        +55.5°C  

```Side note: Ubuntu 11.10 builds sbs as a separate kernel module, so sensors-detect shouldn't show that warning from then on.

---

