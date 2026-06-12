---
title: "How to lower my CPU Fan Speed?"
date: 2012-11-01
forum: Hardware
---

### Post by schoft on 2012-11-01
I cannot seem to control my fanspeed from Ubuntu. My CPU fan is always on 100% (2100RPM) and makes a lot of noise which makes me want to switch to Windows because it'll at least be quiet there.

Tried this:

```
sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/3.2.0-29-generic/kernel/drivers/hwmon/it87.ko): No such device

```And this

```
sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

Here is the output of 'sensors-detect':
```
sudo sensors-detect 
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: ASUSTEK COMPUTER INC P5W DH Deluxe
# Board: ASUSTeK Computer INC. P5W DH Deluxe

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
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
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
Found `Winbond W83627EHF/EF/EHG/EG Super IO Sensors'        Success!
    (address 0x290, driver `w83627ehf')
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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: nouveau-0000:06:00.0-2 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: nouveau-0000:06:00.0-0 (i2c-1)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: nouveau-0000:06:00.0-8 (i2c-2)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `SMSC EMC1023'...                               No
Probing for `SMSC EMC1043'...                               No
Probing for `SMSC EMC1053'...                               No
Probing for `SMSC EMC1063'...                               No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: nouveau-0000:06:00.0-6 (i2c-3)
Do you want to scan it? (YES/no/selectively): yes

Now follows a summary of the probes I have just done.
Just press ENTER to continue:    

Driver `w83627ehf':
  * ISA bus, address 0x290
    Chip `Winbond W83627EHF/EF/EHG/EG Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
w83627ehf
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK


```

Asus p5w DH-Deluxe motherboard. PWM set in BIOS. Anyone have an idea?

---

### Post by schoft on 2012-11-01
Solved it by adding 

```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
```In /etc/default/grub

update grub2 after that "sudo update-grub2"

after rebooting "sudo sensors-detect", and "sudo pwmconfig" should work.

---

