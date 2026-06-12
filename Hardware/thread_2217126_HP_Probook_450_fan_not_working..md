---
title: "HP Probook 450 fan not working."
date: 2014-04-15
forum: Hardware
---

### Post by vroyibg on 2014-04-15
Fan never work in ubuntu (work well in Windows 7) make my laptop overheating. I don't know why. I try many solution from internet but it still not working.
acpitool -f
```
hai@Hai-Pc:~$ acpitool -f
  Fan            : <not available>

```
```
hai@Hai-Pc:~$ lsmod | grep fan
hai@Hai-Pc:~$ 


```
Kernel
```
hai@Hai-Pc:~$ uname -r
3.13.0-24-generic


```
lm_sensors can't detect fan
```
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: Hewlett-Packard HP ProBook 450 G0 [A2018CD200] (laptop)
# Board: Hewlett-Packard 1949

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
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x0701
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
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: DPDDC-D (i2c-6)
Do you want to scan it? (YES/no/selectively): 

Next adapter: Radeon i2c bit bus 0x90 (i2c-7)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x91 (i2c-8)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x92 (i2c-9)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x93 (i2c-10)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x94 (i2c-11)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x95 (i2c-12)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x96 (i2c-13)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: Radeon i2c bit bus 0x97 (i2c-14)
Do you want to scan it? (yes/NO/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

Unloading i2c-dev... OK
Unloading cpuid... OK

hai@Hai-Pc:~$ 


```
sensors result
```
hai@Hai-Pc:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +40.0°C  (crit = +128.0°C)
temp4:        +46.0°C  (crit = +128.0°C)
temp5:         +0.0°C  (crit = +128.0°C)
temp6:       +127.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +50.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +47.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +47.0°C  (high = +87.0°C, crit = +105.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:       +511.0°C  (crit = +120.0°C, hyst = +90.0°C)



```
Thanks.
My english is not very good :)

---

### Post by vroyibg on 2014-04-15
Nobody know?
May be my laptop is not supported.

---

### Post by idodos on 2014-04-19
You seem to have a similar if not exactly the same issue as I had.
Take a look:

[http://ubuntuforums.org/showthread.php?t=2217658]("http://ubuntuforums.org/showthread.php?t=2217658")

---

