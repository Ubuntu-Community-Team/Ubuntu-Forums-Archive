---
title: "Dell Latitude D610 - Fan Control"
date: 2013-07-30
forum: Hardware
---

### Post by qwikrazor87 on 2013-07-30
Hello everyone.
I have a Dell Latitude D610 laptop running Xubuntu 12.04.2 LTS Precise Pangolin.
I am having some trouble figuring out how to manually speed up my fan, it gets a little too hot for comfort and the fan runs too slow all the time.
For the past few months I've been looking for solutions but none of them have worked for me so far.
I tried out lm-sensors, fancontrol, pwmconfig, etc., none have worked.

I have also checked the BIOS settings but found nothing to control the fan.

Here is the entire output from running sensors-detect.
```
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Dell Inc. Latitude D610 (laptop)
# Board: Dell Inc. 0C4708

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
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x1d01
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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: Radeon i2c bit bus DVI_DDC (i2c-0)
Do you want to scan it? (YES/no/selectively): y
 
Next adapter: Radeon i2c bit bus VGA_DDC (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus MONID (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus I801 adapter at 10c0 (i2c-3)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.
```

Here is the output from running pwmconfig.
```
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

I would greatly appreciate some help with this.
Thanks.

---

### Post by Toz on 2013-07-31
You could give the i8k driver a try. Have a look [here]("http://manpages.ubuntu.com/manpages/precise/man1/i8kctl.1.html") and [here]("http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/") for more information.

---

### Post by qwikrazor87 on 2013-07-31
You are awesome man, thanks a bunch for the help. I have control over my fan now. :)

---

