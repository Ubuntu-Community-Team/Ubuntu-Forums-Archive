---
title: "CPU temperature"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by cccc on 2008-02-04
hi

howto check CPU temperature under ubuntu gutsy ?

greetings
cccc

---

### Post by Cannaregio on 2008-02-04
Duh: [http://www.google.com/search?hl=en&rls=com.ubuntu%3Aen-US%3Aofficial&hs=b8S&q=ubuntu+check+CPU+temperature&btnG=Search]("http://www.google.com/search?hl=en&rls=com.ubuntu%3Aen-US%3Aofficial&hs=b8S&q=ubuntu+check+CPU+temperature&btnG=Search")
But since we are supposed to help:

```
acpi -t
```

note that you might as well do ```
acpi -V
```

or, for a more complete info:

```
sudo apt-get install lm-sensors
```

But see the link at the top for more stuff.

---

### Post by pbrane on 2008-02-04
if you just want to check temps now and then:

cat /proc/acpi/thermal_zone/THM/temperature

will give you current temperature in Celsius

---

### Post by Cannaregio on 2008-02-05
> **pbrane said:**
> if you just want to check temps now and then:

```
cat /proc/acpi/thermal_zone/THM/temperature
```

will give you current temperature in Celsius

There's a typo in your addition (at least for my gutsy configuration).
It should be
```
cat /proc/acpi/thermal_zone/TH[COLOR="Blue"]R[/COLOR]M/temperature
```

---

### Post by aethralis on 2008-02-05
The thermal zones can be (and are) different on different machines. My thermal zone is for example

```
cat * /proc/acpi/thermal_zone/TZ00
```

---

### Post by cccc on 2008-02-05
it doesn't work on my GUTSY workstation GX260 from DELL:```

# acpi -t
No support for device type: thermal
# acpi -V
No support for device type: thermal
# cat /proc/acpi/thermal_zone/THRM/temperature
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
# cd /proc/acpi/thermal_zone
root@ania:/proc/acpi/thermal_zone# ls -la
razem 0
dr-xr-xr-x  2 root root 0 2008-02-05 23:14 .
dr-xr-xr-x 11 root root 0 2008-02-05 22:33 ..
root@ania:/proc/acpi/thermal_zone# 

``` 
maybe my mainboard or BIOS is not supported ?

---

### Post by jpittack on 2008-02-05
Dell doesn't bother putting too many sensor in.  They give you a computer and expect you to not touch it.  Since the BIOS from dell don't allow overclocking, why would you need sensors?  I have two sensor in my dell laptop, only one put in by dell.  Since you have a desktop, they just run the fans and call it good.

Sorry.  But don't worry, Dell cheats you out of much more.  I don't have c-states in my laptop.

---

### Post by Yellow Pasque on 2008-02-05
If it's a desktop, try lm-sensors.
```
sudo apt-get install lm-sensors
sudo sensors-detect
```

---

### Post by cccc on 2008-02-05
> **Temüjin said:**
> If it's a desktop, try lm-sensors.
```
sudo apt-get install lm-sensors
sudo sensors-detect
```

I've installed but what are next steps ?

---

### Post by Yellow Pasque on 2008-02-05
Did you run sensors-detect and answer 'y' to the probe questions? Did it find any sensors?
If so, you should just be able to type: sensors
That should give you output from the detected sensors.
If you want to install a Gnome front-end for this (you can add hddtemp on the end of the line if you want to monitor hard disk temps too):
```
sudo apt-get install libsensors3 sensors-applet
```

Now you should be able to right-click on any Gnome panel (the bar at the top or bottom) and select 'Add to panel'. Then, select the Hardware Sensors Monitor (in the System & Hardware section) and click the Add and Close buttons.
You may then have to right-click on "No Sensors Detected!" and select Preferences to set it up.

---

### Post by cccc on 2008-02-06
> **Temüjin said:**
> Did you run sensors-detect and answer 'y' to the probe questions? Did it find any sensors?

YES
```

# sensors-detect
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801DB ICH4
Use driver `i2c-i810' for device 0000:00:02.0: Intel 82845G GMCH

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
Module `i2c-i810' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: I810/I815 I2C Adapter (i2c-0)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: I810/I815 DDC Adapter (i2c-1)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus I801 adapter at dc80 (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
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
Do you want to scan the ISA I/O ports? (YES/no): YES
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
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x6701
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): YES
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```



> **Temüjin said:**
> 
If so, you should just be able to type: sensors
That should give you output from the detected sensors.
If you want to install a Gnome front-end for this (you can add hddtemp on the end of the line if you want to monitor hard disk temps too):
```
sudo apt-get install libsensors3 sensors-applet
```

Now you should be able to right-click on any Gnome panel (the bar at the top or bottom) and select 'Add to panel'. Then, select the Hardware Sensors Monitor (in the System & Hardware section) and click the Add and Close buttons.
You may then have to right-click on "No Sensors Detected!" and select Preferences to set it up.

is already installed, but I get this error:```

$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

---

### Post by Yellow Pasque on 2008-02-06
I think you're SOL. The gx260 supposedly has an smsc 6701 sensor and I don't see that on the list of supported devices on the lm-sensors page. [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

If it makes you feel any better, I'm still waiting on fan control for my sensor. :(

---

### Post by motin on 2008-02-20
```
sudo apt-get install computertemp
```

This will install a GNOME Applet that monitors your CPU temp

---

### Post by s1337m on 2008-06-17
> **Temüjin said:**
> Did you run sensors-detect and answer 'y' to the probe questions? Did it find any sensors?
If so, you should just be able to type: sensors
That should give you output from the detected sensors.
If you want to install a Gnome front-end for this (you can add hddtemp on the end of the line if you want to monitor hard disk temps too):
```
sudo apt-get install libsensors3 sensors-applet
```

Now you should be able to right-click on any Gnome panel (the bar at the top or bottom) and select 'Add to panel'. Then, select the Hardware Sensors Monitor (in the System & Hardware section) and click the Add and Close buttons.
You may then have to right-click on "No Sensors Detected!" and select Preferences to set it up.

works great! thanks!  but one thing, what do the bar graphs next to the temperatures show?  they go from blue-orange-red, im assuming they are system loads.

---

