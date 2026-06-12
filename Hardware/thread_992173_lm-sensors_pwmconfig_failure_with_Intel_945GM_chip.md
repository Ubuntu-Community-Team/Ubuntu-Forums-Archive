---
title: "lm-sensors pwmconfig failure with Intel 945GM chipset"
date: 2008-11-24
forum: Hardware
---

### Post by Nycticorax on 2008-11-24
I want to use lm-sensors (fancontrol) to control my processor fan which I believe is unnecessarily active. However, pwmconfig fails with the message

```
  /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

This is a Fujitsu-Siemens Lifebook S Series laptop which has the an Intel
Core Duo processor with Intel 945GM chipset, and is running Ubuntu
Intrepid (fully updated). My question is: how do I tell whether in principle I can control my fan with this hardware, and if the answer is positive, what is the next step? What follows is what I've learned / done so far.

Looking at the pwmconfig shell-script, the error occurs because there are no pwm* files in the relevant place:

```
~> ls /sys/class/hwmon/hwmon*/device/
/sys/class/hwmon/hwmon1/device/:
driver  hwmon  modalias  name  power  subsystem  temp1_crit  temp1_crit_alarm  temp1_input  temp1_label  uevent

/sys/class/hwmon/hwmon2/device/:
driver  hwmon  modalias  name  power  subsystem  temp1_crit  temp1_crit_alarm  temp1_input  temp1_label  uevent
```

I've looked at [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices), but don't fully
understand the information there. Under SENSOR CHIP DRIVERS there is
this entry

```
Intel   Core, Core 2  yes  coretemp   2.6.22  (2007-03-25) Integrated sensor in CPU. Driver contributed by Rudolf Marek. 

```
Is this good news, or is it saying that there's just temperature stuff
but no fan control?

and under I2C/SMBUS BUS DRIVERS there are several entries for Intel
none of which obviously correspond to my hardware.

I've run sensors-detect which results in (full output at bottom) 

```
Driver `smartbatt' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 18e0'
    Busdriver `i2c-i801', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)
```

This coretemp module is loaded and is providing temperature
readings. I don't know if it has anything to do with fan control.

Running sensors gives

```
~> sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8Â°C  (crit = +100.0Â°C)                  
temp2:       +26.8Â°C  (crit = +100.0Â°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0Â°C  (crit = +100.0Â°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +43.0Â°C  (crit = +100.0Â°C)            

```

(I have not observed the first two temperatures be anything other than
26.8C)

I'd like to be able to modify my fan behaviour but don't know what to
do in order that pwmconfig runs. Thanks very much for any help. Full
output from sensors-detect follows.

Dan

```
Next adapter: SMBus I801 adapter at 18e0 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x0b
Probing for `Smart Battery'...                              Success!
    (confidence 5, driver `smartbatt')
Client found at address 0x19
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6680/MAX6681'...                      No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!



Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown non-standard chip with ID 0x7a
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `smartbatt' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 18e0'
    Busdriver `i2c-i801', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
coretemp
#----cut here----


```

---

### Post by BlueElk on 2009-03-10
*bump* (because I have a similar issue with my HP laptop, though I don't have that 'smartbatt' driver)

---

### Post by rikxik on 2009-05-10
Even I'm facing the same problem of Fans not startig at all with my Core Duo HP nx6320 laptop. The sensors output doesn't have any entry for Fan or RPM:

> 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +256.0°C)                  
temp2:       +54.0°C  (crit = +105.0°C)                  
temp3:       +52.0°C  (crit = +105.0°C)                  
temp4:       +34.7°C  (crit = +105.0°C)                  
temp5:       +40.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +54.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +55.0°C  (crit = +100.0°C)  


Full output of sensors-detect is below (I've already inserted coretemp module but it finds some unknown chipset?):

> 
Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x2600
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown non-standard chip with ID 0x7a

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No


In my previous (Gutsy) setup, I could just do this and the fan ran at full speed:

```

for i in `/proc/acpi/fan/*/state` ; do
   echo "on" > $i
done

```

Now I can't write to these files even as root (error is "echo: write error: Invalid argument") :

> 
[/proc/acpi/fan] $ find -name state -print
./C328/state
./C327/state
./C326/state
./C325/state


I prefer to have the fan running most of the time (fan noise is not an issue for me).

Any pointers will be highly appreciated.

---

### Post by rikxik on 2009-05-11
*bump*

---

