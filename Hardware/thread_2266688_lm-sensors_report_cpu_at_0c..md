---
title: "lm-sensors report cpu at 0c."
date: 2015-02-24
forum: Hardware
---

### Post by azmo35 on 2015-02-24
Hi, all at long time I haven't ask for help but at the moment I'm puzzeled, so hardware Board: Gigabyte Technology Co., Ltd. F2A88X-D3H, cpu A4-6300 and the temp is 0c. thank for any info or help.

 sensors-detect report
```
media-center@mediacenter ~ $ sudo sensors-detect
[sudo] password for media-center: 
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# Board: Gigabyte Technology Co., Ltd. F2A88X-D3H

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
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8620
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
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-1)
Do you want to scan it? (YES/no/selectively): yes

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.sensors
```

Ubuntu 14.04.1 thanks.

---

### Post by MartyBuntu on 2015-02-24
Have you installed proprietary graphics card drivers?

---

### Post by Yellow Pasque on 2015-02-24
^I don't think proprietary graphics drivers will help (it's possible though).

The version of lm-sensors Ubuntu uses might be a bit too old to automatically detect the CPU's sensor. Specifically, it might need this commit: [http://www.lm-sensors.org/changeset/6191/lm-sensors/trunk/prog/detect/sensors-detect](http://www.lm-sensors.org/changeset/6191/lm-sensors/trunk/prog/detect/sensors-detect)
Hopefully, it still works manually. Does the output change if you manually load k10temp module?
```
sudo modprobe -v k10temp
sensors
```

As for the other sensor chip (ITE IT8620E) on the board, see this comment:
> Custom part made by ITE for Gigabyte, no datasheet nor any other information available .... We had a report that the chip is somewhat compatible with the IT8728F for the hardware monitoring part. Be very careful with fan control as it wasn't tested. So you can try loading the it87 driver with force_id=0x8728 and see how it goes. If you do, please report, including the output of "sensors".
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)
```
sudo modprobe -v it87 force_id=0x8728
sensors
```

---

### Post by azmo35 on 2015-02-25
Thanks for the reply  and yes Catalyst 2.20 Driver 13.35.

---

### Post by azmo35 on 2015-02-25
Thanks for the reply, after doing the commands discrived this is the output:
 
```
media-center@mediacenter ~ $ sudo modprobe -v k10temp
media-center@mediacenter ~ $ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

media-center@mediacenter ~ $ sudo modprobe -v it87 force_id=0x8728
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/hwmon/hwmon-vid.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/hwmon/it87.ko force_id=0x8728
media-center@mediacenter ~ $ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

it8728-isa-0228
Adapter: ISA adapter
in0:          +0.92 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.50 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.03 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.03 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.02 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.34 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.46 V  
fan1:        1584 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +21.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:         -8.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +13.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM
```

PS: maybe I use a old kernel and driver.

---

### Post by Yellow Pasque on 2015-02-25
> **azmo35 said:**
> maybe I use a old kernel and driver.

It's not the latest kernel, but I do not see any recent changes that might fix the issue: [https://github.com/torvalds/linux/commits/master/drivers/hwmon/k10temp.c](https://github.com/torvalds/linux/commits/master/drivers/hwmon/k10temp.c)

Perhaps it is simply a fault of the CPU. Check the temperature after you do something that loads the CPU:
> AMD CPUs are known report wildly off temperatures especially at
low temperatures. Does the temperature increase with load?
[http://lists.lm-sensors.org/pipermail/lm-sensors/2014-November/042922.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2014-November/042922.html)

---

### Post by azmo35 on 2015-02-25
Thanks for your reply on other machine that is kind of similar "cpu A4-5300" not the same machine I will test later, if I use the #watch sensors# in terminal and convert a audio file then it goes from 1400mhz to 3400mhz and the temp will go to 22c., so I think is not a cpu or board fault but the way it works.
To anser your question ,,Does the temperature increase with load?,, yes in this machine.

---

### Post by Yellow Pasque on 2015-02-25
>  so I think is not a cpu or board fault but the way it works.
Well, that is still a fault in the CPU, but it's not limited to your specific CPU chip.
I have a Phenom II model that reports about 10C lower than what it really is. *Shrug*

---

### Post by azmo35 on 2015-02-25
Thanks again tested  and in load is only 8.8c. but i noted that on the other machine watch sensors give me mor info like fan speed this one only temp, maybe I need play with bios settings, thanks for all replys.

---

