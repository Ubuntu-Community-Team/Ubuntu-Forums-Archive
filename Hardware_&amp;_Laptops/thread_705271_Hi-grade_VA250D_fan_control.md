---
title: "Hi-grade VA250D fan control"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by davidryderuk on 2008-02-23
Hello,
I i am quite new to Linux and am having trouble getting Ubuntu 7.10 to control my fan speed. At the moment the fan switches on with the grub boot loader at one particular speed but then stays at this speed regardless of the number of programmes running and the corresponding temperature. The temperature reported by the acpi sensor varies from 35 to 52 degrees C, which is far lower than when vista is running where the temperature stays around 65 degrees C. 

I have installed lmsensors (which came up with additional sensors for temperature) and then tried to install pwmconfig but was given the message

 "/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed". 

The last thing to say is that i am running "PhoenixBIOS™ 4.0 Release 6.1" and at start up PCI: bios bug #81 is reported. I have tried the start up option acpi=off and a few others but these either make no difference or they make the computer crash. 

Thanks

---

### Post by mrsteveman1 on 2008-02-23
Have you run sensors-detect?

---

### Post by davidryderuk on 2008-02-23
Yes, i followed the first couple of instructions posted here: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

When sensors-detect was run it seemed to detect one series of sensors which i think are related to the intel dual core processor in my laptop and are referred to as "Intel Core family thermal sensor.....driver coretemp". Then when i type "sensors" into the terminal it comes up with this:

***********************************

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +16°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +16°C  (high =   +85°C)    

*************************************    

When you compare this to the readout from the link above, you can see that the other person has much more information including his fan speed "fan1: 3668 RPM" where as I do not, which i assume is why pwmconfig is not working.

 The only mention of the fan i can find is in System > Preferences > Hardware information where it mentions the fan as fan and mentions its linux acpi path, acpi type and hotplug type etc. 

Thanks for the suggestion

---

### Post by mrsteveman1 on 2008-02-23
If sensors-detect couldn't find the chip it's not the end of the world, there are chips the kernel supports that lm-sensors doesn't yet.

When you ran sensors-detect it probably found an unknown chip (check again) that it couldn't find a module for. What was listed?

---

### Post by davidryderuk on 2008-02-23
Okay i don't really know what a lot of the other text means and i don't want to quote anything out of context so i shall just copy the whole of the information below. The only thing it seems to mention and not load a driver for is the SPD EEPROM which it does detect. 

*************************************
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-viapro' for device 0000:00:11.0: VIA Technologies VT8237A South Bridge

We will now try to load each adapter module in turn.
Module `i2c-viapro' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus Via Pro adapter at 4100 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

---

### Post by mrsteveman1 on 2008-02-23
Sounds like it didn't find anything, all the "trying" lines say no except for the one 
```

Probing for Super-I/O at 0x4e/0x4f
```

But it doesn't say if it found anything.

Are there any files in /proc/acpi/fan/FAN/

---

### Post by davidryderuk on 2008-02-23
Yes, there is a file called state. I have looked at this file before after reading the post below. 

[http://ubuntuforums.org/showthread.php?t=230673](http://ubuntuforums.org/showthread.php?t=230673)

When trying the first part of the post to find the state of the fan it was reported to be switched on, a fact that was correct. However after suspension when my fan goes from on to off regardless of temperature the state of the fan is shown to be on as well. (i  understand that keeping a computer on whilst the fan is completely switched off is dangerous, which is why i had a temperature monitoring app running in the background during this process).

---

