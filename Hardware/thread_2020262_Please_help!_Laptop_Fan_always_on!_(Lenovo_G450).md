---
title: "Please help! Laptop Fan always on! (Lenovo G450)"
date: 2012-07-08
forum: Hardware
---

### Post by toufel on 2012-07-08
So I have just installed Xubuntu 12.04 on my Lenovo G450 laptop and the fan just doesn't go off! (Even when the system is idle)

**My System Configuration**
Pentium Dual-Core T4300 (2.10GHz)
1 GB DDR3 RAM
Mobile Intel 4 Series Express Chipset Family

(I am running Xubuntu with **Wubi**)

Please help!:)

---

### Post by robtygart on 2012-07-08
Do you know what your CPU temptures are?

---

### Post by toufel on 2012-07-08
I installed hardinfo but the sensors list is showing nothing. How do I check the CPU temperature?

---

### Post by robtygart on 2012-07-08
> **toufel said:**
> I installed hardinfo but the sensors list is showing nothing. How do I check the CPU temperature?

Same here! I was looking for a different one. 

I am wondering if its because of high temptures or maybe your fan control program is not working.

---

### Post by Redblade20XX on 2012-07-08
First, what graphics card do you have? Do you have the proprietary driver installed or the open-source one? Usually the proprietary ones have better temperature mangement.


Secondly, have you tried lm-sensors?

See here: [http://lm-sensors.org/](http://lm-sensors.org/)

In the terminal type,
```
sudo apt-get update
```
```
sudo apt-get install lm-sensors
```

After the installation, type this in the terminal to set it up.

```
sensors-detect
```

This will load any modules in the kernel that is needed for temperature readings.
It will also determine if sensing system is working.

-Red

---

### Post by toufel on 2012-07-08
RedBlade,
I have Intel Integrated Graphics on my laptop (I do not have a discrete graphics card). No 'Additional Drivers' drivers show up.

I installed lm-sensors 
and ran sensors-detect

What do I do then?
Some modules are brought up asking me a yes/no. Do I hit Y and Enter?

---

### Post by Redblade20XX on 2012-07-08
> **toufel said:**
> RedBlade,
I have Intel Integrated Graphics on my laptop (I do not have a discrete graphics card). No 'Additional Drivers' drivers show up.

I installed lm-sensors 
and ran sensors-detect

What do I do then?
Some modules are brought up asking me a yes/no. Do I hit Y and Enter?

It should be safe to select 'Y' for all the options given. After it has finished, type in the terminal,

```
sensors
```

and post the result of the command.

-Red

---

### Post by toufel on 2012-07-08
setonfire@ubuntu:~$ sensors-detect
The program 'sensors-detect' is currently not installed.  You can install it by typing:
sudo apt-get install lm-sensors
setonfire@ubuntu:~$ sudo apt-get install lm-sensors
[sudo] password for setonfire: 
Sorry, try again.
[sudo] password for setonfire: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 188 not upgraded.
Need to get 99.9 kB of archives.
After this operation, 404 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe lm-sensors i386 1:3.3.1-2ubuntu1 [99.9 kB]
Fetched 99.9 kB in 1s (58.5 kB/s)     
Selecting previously unselected package lm-sensors.
(Reading database ... 154745 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a3.3.1-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up lm-sensors (1:3.3.1-2ubuntu1) ...
setonfire@ubuntu:~$ sensors-detect
You need to be root to run this script.
setonfire@ubuntu:~$ sudo sensors-detect
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: LENOVO 2949 (laptop)
# Board: LENOVO NITU1

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
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
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
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
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus disabled (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus ssc (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOB (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus vga (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOA (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus panel (i2c-5)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4f
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6642'...                              No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: i915 GPIOC (i2c-6)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4f
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6642'...                              No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: i915 gmbus dpc (i2c-7)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOD (i2c-8)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpb (i2c-9)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOE (i2c-10)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus reserved (i2c-11)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpd (i2c-12)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOF (i2c-13)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-B (i2c-14)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-D (i2c-15)
Do you want to scan it? (YES/no/selectively): y

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

Do you want to add these lines automatically to /etc/modules? (yes/NO)n

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

[B]setonfire@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +41.0°C  (crit = +119.0°C)[/B]

setonfire@ubuntu:~$

---

### Post by Redblade20XX on 2012-07-09
Alright so you got some information.

First, make sure your BIOS is up to date. Then check in the BIOS to see if there is any fan/temperature control settings or reported information. They are usually in the advanced menu of the BIOS.

If there isn't any menu as such, try looking into acpi and passing some kernel parameters on boot.

Take a look here for acpi: 

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

And here for the kernel parameters:

[https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

Make sure to read the kernel parameters stated in the second link at the bottom of the page!

- Red

---

### Post by ronnysingh on 2012-07-09
That was a problem in my Lenovo laptop. The fan seemed to be running all the time anbd it also made some noise. As far as I know, laptop fans run like that to cool the excessive temperature of CPU.

---

### Post by americanman28 on 2012-07-12
try the bios

---

