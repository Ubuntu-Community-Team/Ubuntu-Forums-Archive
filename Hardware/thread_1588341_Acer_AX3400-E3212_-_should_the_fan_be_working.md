---
title: "Acer AX3400-E3212 - should the fan be working?"
date: 2010-10-04
forum: Hardware
---

### Post by Robert.Thompson on 2010-10-04
Hello:

I just bought an Acer AX3400-E3212, blew out windows 7 and installed Ubuntu 64-bit.

I see that the fan is not turning - is it suppose to turn at all times?

If so, how do I tell ubuntu 64-bit to do that?

Thank you,

---

### Post by gordintoronto on 2010-10-04
The fan should run when the computer gets hot.

Install LM-sensors and run sensors-detect. If it does not support your CPU, install Ubuntu 10.10, which supports AMD K10 processors for reporting the temperature. Running just "sensors" will tell you the CPU temperature. There's also an applet which you can install on the Panel which will show temperatures. But first, the kernel has to support that aspect of your CPU.

---

### Post by Robert.Thompson on 2010-10-05
> **gordintoronto said:**
> The fan should run when the computer gets hot.

Install LM-sensors and run sensors-detect. If it does not support your CPU, install Ubuntu 10.10, which supports AMD K10 processors for reporting the temperature. Running just "sensors" will tell you the CPU temperature. There's also an applet which you can install on the Panel which will show temperatures. But first, the kernel has to support that aspect of your CPU.

Hi Gary:

Here is the terminal output:
rob@rob-desktop:~$ sudo sensors-detect
[sudo] password for rob: 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Acer Aspire X3400

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
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
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
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0xa10, driver `it87')
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
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-nforce2' for device 0000:00:01.1: nVidia Corporation nForce SMBus (MCP78S)
Module i2c-dev loaded successfully.

Next adapter: SMBus nForce2 adapter at 4d00 (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): yes

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0xa10
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK

rob@rob-desktop:~$ sensors
it8720-isa-0a10
Adapter: ISA adapter
in0:         +1.02 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.33 V  (min =  +4.06 V, max =  +4.08 V)   ALARM
in5:         +1.15 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.07 V
fan1:       1339 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +31.0°C  (low  = -17.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +38.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:      -128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +0.375 V

rob@rob-desktop:~$ 

My fan is not running at present, should it be?

I appreciate any time you might take to help me.

BTW, want do you mean by the "Pascal?" reference in the other post?

Thanks again,

---

### Post by gordintoronto on 2010-10-05
If temp1 or temp2 is your CPU, it's not hot enough to run the fan at high speed. Sensors says your fan is running, at not much more than idle. Temperatures below 50 C are fabulous.

I assume there's also a fan in your power supply, but no case fan blowing air out the back? That's unusual these days.

By the way, your hard drive can probably also report its temperature, using a program called hddtemp.

What version of Ubuntu are you using? (10.10?)

I'm an IT guy, and the last time I heard anybody mention Pascal was more than 20 years ago.

---

### Post by Robert.Thompson on 2010-10-05
> **gordintoronto said:**
> If temp1 or temp2 is your CPU, it's not hot enough to run the fan at high speed. Sensors says your fan is running, at not much more than idle. Temperatures below 50 C are fabulous.

I assume there's also a fan in your power supply, but no case fan blowing air out the back? That's unusual these days.

By the way, your hard drive can probably also report its temperature, using a program called hddtemp.

What version of Ubuntu are you using? (10.10?)

I'm an IT guy, and the last time I heard anybody mention Pascal was more than 20 years ago.

Hi Gord:

I am using Ubuntu 10.04 LTS 64-bit.

Yes, there is air blowing out. It is just sooo quite! I guess this has all been a false-alarm - I used to alot of noise from my 12 year old Dell. :)

I used Delphi (Object Pascal) to build an accounts receivable and loan database system for my, now defunct, employer. We used Delphi for the front end and Interbase for the database. I built the original system using flat files (paradox etc) and then I hired a real live programmer after a few years of growth to put the whole thing on Interbase - it worked out real well.

I guess the meteorite missed me - I plan to build a golf application using Lazarus (Object Pascal) and Firebird during my 'between jobs' time.

Thanks, again, for all your help.

---

