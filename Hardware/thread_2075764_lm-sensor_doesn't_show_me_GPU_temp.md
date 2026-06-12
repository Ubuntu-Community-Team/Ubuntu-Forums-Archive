---
title: "lm-sensor doesn't show me GPU temp"
date: 2012-10-24
forum: Hardware
---

### Post by Normal01 on 2012-10-24
Hello all,
I have a little problem. I have a PC(ASUS EeePC 1215B with AMD C-60 and Radeon HD 6290) with Ubuntu 12.04 64bit.

When i write on terminal ```
sudo sensor-detect
``` the output is:
```

[sudo] password for matteo: 
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: ASUSTeK Computer INC. 1215B (laptop)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   Success!
    (driver `k10temp')
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 12h and 14h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK
Unloading cpuid... OK

```

and when I write ```
sudo sensors
``` terminal show me this:
```
sudo sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +55.9°C  (high = +70.0°C)
                       (crit = +100.0°C, hyst = +97.0°C)

```

Now, why PC doesn't load GPU and CPU temp?
Thank's a lot.

---

### Post by PPN13 on 2012-10-26
You need to compile [Psesnor](http://wpitchoune.net/blog/psensor/) yourself and to have the libatiadlxx on your system. I 've done it in the past but unfortunately I can't remember details right now. I am also at a PC with a nvidia cardright now so I can't test things.. 

It worked though on my desktop with my 4870 and later 7770, didn't even have to change anything after swapping GPUs.


EDIT:

[This](http://wpitchoune.net/blog/news_experimental-ati-monitoring-support/) is useful

---

### Post by sffvba[e0rt on 2012-10-26
From AskUbuntu I see you could try running;

```
aticonfig --odgt
```



404

---

### Post by Linuxisfast on 2012-10-26
You don't need lm sensors to display gpu temps, all you need to do is install the proprietary catalyst on the system and acpi will show you the gpu temps, you can then use indicator-sensors from alex murray to display it right in your top panel. I have the same netbook but in smaller 10' display and this is how I monitor the GPU temp.

---

### Post by Normal01 on 2012-10-26
Thank's everybody.
It's strange, because yesterday "Hardware Sensor Indicator" didn't show me the temp of GPU. I don't know why it happened.
But now, "temp1" is the temp of CPU or the temp of motherboard?

---

### Post by sffvba[e0rt on 2012-10-26
From this it would seem it is the CPU - [http://www.kernel.org/doc/Documentation/hwmon/k10temp](http://www.kernel.org/doc/Documentation/hwmon/k10temp)


404

---

### Post by Normal01 on 2012-10-26
Thank you so much.
If I understand right, "temp1" is a temp of CPU. Very good. 
Thank's a lot. :-D
Good night.

---

