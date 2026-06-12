---
title: "lm-sensors does not show cpu temps"
date: 2012-02-28
forum: Hardware
---

### Post by Blah91 on 2012-02-28
Hey, I can't get lm-sensors show my CPU temps at all. 
So what I have done: installed lm-sensors via *"sudo apt-get install lm-sensors"* > *"sudo sensors-detect"* > answered yes to all except no to last one (I'v tried also answering yes to last one but no change) > *"sudo /etc/init.d/module-init-tools restart*" & rebooting.

After doing above, I ran *"sensors"*:
```

****:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +18.9Â°C  (high = +70.0Â°C)

```I'd like to know my CPU temps but lm-sensors simply does not show them. 

Contents of */etc/modules*
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

```Specs if matters:
Ubuntu 11.10 (GNU/Linux 3.0.0-16-server x86_64)
AMD Phenom 960T, four cores (no unlocking done)
ASROCK AM3/AM3+ AMD880G

I have also tried downloading and installing lm-sensors from their website (I purged lm-sensors from my system before that) but it didn't help. 

I could use some help now.

---

### Post by Yellow Pasque on 2012-02-28
Can you give the full output of sensors-detect?

---

### Post by Blah91 on 2012-02-28
> **Temüjin said:**
> Can you give the full output of sensors-detect?

```
****:~$ sudo sensors-detect
[sudo] password for ****:
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: To Be Filled By O.E.M. To Be Filled By O.E.M.
# Board: ASRock 880GMH/U3S3

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
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             No
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
Found `Nuvoton W83677HG-I (NCT6771F/NCT6772F/NCT6775F) Super IO Sensors'Success!
    (address 0x290, driver `to-be-written')
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
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): no
Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton W83677HG-I (NCT6771F/NCT6772F/NCT6775F) Super IO Sensors' (confidence: 9)

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Note: there is no driver for Nuvoton W83677HG-I (NCT6771F/NCT6772F/NCT6775F) Super IO Sensors yet.
Check http://www.lm-sensors.org/wiki/Devices for updates.

No modules to load, skipping modules configuration.

Unloading cpuid... OK


```

---

### Post by Yellow Pasque on 2012-02-28
Try this: [https://github.com/groeck/w83627ehf/tarball/master](https://github.com/groeck/w83627ehf/tarball/master)

Extract it, cd to that directory and run:
```
make
sudo make install
sudo modprobe w83627ehf
sensors
```

---

### Post by Blah91 on 2012-02-28
> **Temüjin said:**
> Try this: [https://github.com/groeck/w83627ehf/tarball/master](https://github.com/groeck/w83627ehf/tarball/master)

Extract it, cd to that directory and run:
```
make
sudo make install
sudo modprobe w83627ehf
sensors
```
Oooh... it's working! Thanks!

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +19.4Â°C  (high = +70.0Â°C)

nct6775-isa-0290
Adapter: ISA adapter
Vcore:        +1.34 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +1.70 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:        +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:          +0.10 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:          +1.89 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:          +0.10 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:         +3.47 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:         +3.44 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:        1068 RPM  (min =    0 RPM, div = 8)  ALARM
fan2:           0 RPM  (min =    0 RPM, div = 16)
fan3:        1068 RPM  (min =    0 RPM, div = 8)  ALARM
fan4:           0 RPM  (div = 16)
SYSTIN:       +36.0Â°C  (high =  +0.0Â°C, hyst =  +0.0Â°C)  ALARM  sensor = thermistor
CPUTIN:       +32.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = thermistor
AUXTIN:      +126.5Â°C  (high = +114.0Â°C, hyst = +114.0Â°C)  ALARM  sensor = thermistor
cpu0_vid:    +0.475 V
intrusion0:  ALARM


```

Now I can stress test my cpu and see if my cooler is working as intended...

---

### Post by Yellow Pasque on 2012-02-28
You're welcome. Add "w83627ehf" (no quotes) to /etc/modules so the module loads at every boot. Also, if you install a new kernel, be sure to run 'make install' again.

---

