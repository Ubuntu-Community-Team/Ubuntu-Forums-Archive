---
title: "lm_sensors not detecting fans on z170 skylake platform"
date: 2016-04-25
forum: Hardware
---

### Post by cloud7 on 2016-04-25
Hello people. I'm having a problem with my fans as they seem to spin up and down erratically based on my system load e.g. starting up firefox make them go like 75% and loud and once it's loaded they become silent again. On windows I had a proprietary software called AISuite 3 in which I could set the "spin up" time to circumvent this issue and it worked really well.

Now here's the problem, on ubuntu I guess my only option is lm_sensors with fancontrol, however "sensors-detect" does not seem to detect my hardware.

  here's the output of "sensors-detect"

```
# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)
# Board: ASUSTeK COMPUTER INC. Z170 PRO GAMING
# Kernel: 4.4.0-21-generic x86_64
# Processor: Intel(R) Core(TM) i5-6600K CPU @ 3.50GHz (6/94/3)

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
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xd121
    (logical device B has address 0x290, could be sensors)
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
Found unknown SMBus adapter 8086:a123 at 0000:00:1f.4.
Sorry, no supported PCI bus adapters found.

Next adapter: NVIDIA i2c adapter 0 at 1:00.0 (i2c-0)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter 2 at 1:00.0 (i2c-1)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter 5 at 1:00.0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter 6 at 1:00.0 (i2c-3)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter 8 at 1:00.0 (i2c-4)
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

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK


```


Here's the output of "sensors"

```
 sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +34.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:         +28.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:         +31.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:         +29.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:         +28.0°C  (high = +80.0°C, crit = +100.0°C)

asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM


```

Initially back when I was using ubuntu 15.10 I thought that kernel was the problem but after upgrading to the newest LTS nothing changed. Any suggestions?

---

### Post by cloud7 on 2016-04-26
bump

"revision 6284 (2015-05-31 14:00:33 +0200)" might be the problem but sadly the project seems to be abandoned and it looks like there's no alternative?

---

### Post by pqwoerituytrueiwoq on 2016-04-26
for my Z97 based system i had to add a line to /etc/modules
```
nct6775
```
if i only knew what voltages i was looking at... fans are easy to determine

---

### Post by cloud7 on 2016-04-29
Doesn't work for me unfortunately.. Is there any other way of controlling fans apart from "fancontrol"?

---

### Post by Yellow Pasque on 2016-04-29
[http://www.spinics.net/lists/lm-sensors/msg44015.html](http://www.spinics.net/lists/lm-sensors/msg44015.html)

You may have to grab a copy of the nct6775 code and hack it, changing d120 to d121
[https://github.com/groeck/nct6775](https://github.com/groeck/nct6775)
[https://github.com/groeck/nct6775/blob/master/nct6775.c#L120](https://github.com/groeck/nct6775/blob/master/nct6775.c#L120)

---

### Post by Yellow Pasque on 2016-04-29
> **cloud7 said:**
> Doesn't work for me unfortunately.. Is there any other way of controlling fans apart from "fancontrol"?

fancontrol uses standard PWM method, but your sensor chip has to be supported first.

---

### Post by cloud7 on 2016-04-30
That driver doesn't work even with the mentioned hack.. damn.. Next time I will really think twice before buying an asus motherboard again

---

### Post by xkalibur on 2016-09-22
Hey Guys,

I have a new Skylake Z170 build (Asus Z170i mobo) and I'm having the same issue.. Only the coretemp module is working.

This is what I got from sensors-detect for the I2C/SMBus adapter:
```
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Found unknown SMBus adapter 8086:a123 at 0000:00:1f.4.
Sorry, no supported PCI bus adapters found.

```

I did a quick google search which answered my question..
```
sudo modprobe -v nct6775
``` will load the motherboard information. Then add the line nct6775 to your /etc/modules file so that it's available after reboot.

See this post:
[https://forums.linuxmint.com/viewtopic.php?t=221577](https://forums.linuxmint.com/viewtopic.php?t=221577)

xk

---

