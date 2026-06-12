---
title: "getting lm-sensors to display correct temps for amd64"
date: 2008-10-31
forum: General Help
---

### Post by m_l17 on 2008-10-31
I installed lm-sensors and ran sudo sensors-detect. It only detects k8temp, but the temps displayed are low 10-12C. Under heavy load it goes into the 30-40C or so. I have read the lm-sensors thread but that didn't help. How can I set it up so it displays the correct temps?

---

### Post by dcstar on 2008-10-31
> **m_l17 said:**
> I installed lm-sensors and ran sudo sensors-detect. It only detects k8temp, but the temps displayed are low 10-12C. Under heavy load it goes into the 30-40C or so. I have read the lm-sensors thread but that didn't help. How can I set it up so it displays the correct temps?

"Brisbane" core Athlon 64s do this. Don't use the CPU diode temps, use your motherboard CPU temp sensor.

---

### Post by m_l17 on 2008-10-31
How do I go about using the motherboard CPU temp sensor?

---

### Post by m_l17 on 2008-10-31
Here is the output of sensors and sudo sensors-detect:

```
ml ~ $  sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +12.0°C  (crit = +95.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +17.0°C                                    
Core0 Temp:  +10.0°C                                    
Core1 Temp:  +15.0°C                                    
Core1 Temp:   +2.0°C                                    

ml ~ $  sudo sensors-detect
[sudo] password for ml: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): ye
Probing for PCI bus adapters...
Use driver `i2c-nforce2' for device 0000:00:01.1: nVidia Corporation nForce4 SMBus (MCP61)

We will now try to load each adapter module in turn.
Module `i2c-nforce2' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus nForce2 adapter at 1c00 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: SMBus nForce2 adapter at 1c40 (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Asus F8000 Super IO'                                 Success!
    (address 0x295, driver `f8000')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `f8000' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x295
    Chip `Asus F8000 Super IO' (confidence: 9)

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# Warning: the required module f8000 is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
f8000
k8temp
#----cut here----

Do you want to add these lines automatically? (yes/NO)


```

---

### Post by dcstar on 2008-10-31
> **m_l17 said:**
> Here is the output of sensors and sudo sensors-detect:

```
ml ~ $  sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +12.0°C  (crit = +95.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +17.0°C                                    
Core0 Temp:  +10.0°C                                    
Core1 Temp:  +15.0°C                                    
Core1 Temp:   +2.0°C                                    

ml ~ $  sudo sensors-detect
[sudo] password for ml: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)
......
To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# Warning: the required module f8000 is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
f8000
k8temp
#----cut here----

**Do you want to add these lines automatically? (yes**/NO)


```

Just have it add those lines, reboot and then see if your motherboard temps are now available.

Anyway, if you use the Gnome sensors-applet you can just add a 20C offset to the CPU diode temps and that gets them just about correct.

---

### Post by m_l17 on 2008-11-01
> Just have it add those lines, reboot and then see if your motherboard temps are now available.


I already have done that but still get same values.  

> Anyway, if you use the Gnome sensors-applet you can just add a 20C offset to the CPU diode temps and that gets them just about correct.

Is there a way I can do the same with conky? I prefer to use conky and I'am using Xubuntu. Thank You for the suggestion.

---

### Post by darkcrawler on 2008-11-04
are you using the 2.6.27-7 Kernel?
I have a similar problem with my lm-sensors and conky..

---

### Post by m_l17 on 2008-11-05
yes

ml ~ $  uname -a

Linux amd 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

---

### Post by darkcrawler on 2008-11-05
Same for me, with the last Kernel was all right, with the 2.6.27-7 the CPU temp displayed by lm-sensors is 15-16°C higher..

---

### Post by m_l17 on 2008-11-05
This  is the only install I have done on this system [8.10], I can't comment on previous installs. I have searched for 
a solution, but have not found one yet. If I find a solution I will post it here.

---

### Post by darkcrawler on 2008-11-14
Still no solution for me.. :(

---

### Post by m_l17 on 2008-11-14
me to :(

---

