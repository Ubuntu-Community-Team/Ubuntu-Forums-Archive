---
title: "lm-sensors and the Acer Aspire One"
date: 2008-10-21
forum: Hardware
---

### Post by eks on 2008-10-21
Hellos,

I've installed the stuff to manage the fan, but I'm a bit weary of always loading the script at boot without some visual feedback from the actual temperature of the CPU.

Problem is I've tried and searched what seems every possible way to have some kind of temperature sensor without success.

I'm actually using Xubuntu (Intrepid Beta) on the AAO, but tried both xfce4 native sensors and Gnome sensors. Both seem to use lm-sensor, which gives me this when I do a "sensors-detect":

```
$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y  
Module loaded successfully.
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

Next adapter: SMBus I801 adapter at 6000 (i2c-0)
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
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
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
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

Is there a way to make lm-sensors work?

Or is there another software to detect temperature besides lm-sensors?

---

### Post by teaker1s on 2008-10-21
[here :guitar:]("https://help.ubuntu.com/community/SensorInstallHowto") also have you seen the ubuntu [aspire one docs.]("https://help.ubuntu.com/community/AspireOne") acerfand is fine

---

### Post by TuxPrincess on 2008-10-21
I currently have ubuntu 7.10 installed on my laptop and use the sensors applet which displays the temperature output by my acpi on the panel.

If you run the acpi -t command in a terminal window then it should display your acpi temperature.

hope that helps :-)

---

