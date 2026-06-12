---
title: "Laptop fan stops after suspend."
date: 2010-05-15
forum: Hardware
---

### Post by jaansson on 2010-05-15
Hello!

I've been looking around for a solution for this for a while. My fan stops when coming back from suspend. This happens almost everytime. I've found a lot of information about fan going full speed after suspend. That used to happen from time to time before, but now it's the other way around. This causes my laptop to become very hot, so I have to restart it to make it work again.

However, when it reaches about 75-80 degrees it starts going full speed to cool it down. But when it's down at like 60 degrees again it stops. So basically it starts every ~10 minutes when just doing minor things such as browsing.

Are there any solution for this?

---

### Post by jaansson on 2010-05-15
No ideas?

---

### Post by jaansson on 2010-05-22
Just found that when running 'sensors' I get the following output:


```
danne@danne-laptop:~$ sudo sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:      +256.0°C  (crit = +105.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +75.0°C  (high = +70.0°C, crit = +100.0°C)  

danne@danne-laptop:~$ 
```

I assume that means the first thing gets totally freaked out after a suspend? Because before the suspend they both show the same. Is there a way to make the computer listen to the k10temp instead?

---

### Post by jaansson on 2010-05-24
Okay, this is really getting on my nerves. Now it happened when I started the computer from scratch. And the 'sensors' shows normal values. Isn't there really any way to restart the sensors or fans or anything?

---

### Post by dino99 on 2010-05-24
which laptop are you talking about ?

check the bios settings about powersaving and search for a bios update

have you run sensors-detect ?

---

### Post by jaansson on 2010-05-25
It's a HP 6735s. Heard some of these HP's have problems with fans in Ubuntu, but mostly heard it's the other way; that the fan is going full speed.

Okay, I'll try a BIOS update and see what happens.

Yep, ran sensors-detect a few times. Here is what I get, but looks alright to me.

```
danne@danne-laptop:~$ sudo sensors-detect
[sudo] password for danne: 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Hewlett-Packard HP Compaq 6735s (laptop)
# Board: Hewlett-Packard 30E4

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           Success!
    (driver `k10temp')
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x4501
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
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
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
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
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6649/MAX6692'...              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Winbond W83L771AWG/ASG'...                     No
Probing for `Texas Instruments TMP401'...                   No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments TMP423'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Analog Devices ADT7481'...                     No
Probing for `Fintek F75383S/M'...                           No
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
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
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6647'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM64'...                No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 11h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK

danne@danne-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:      +256.0°C  (crit = +105.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +58.1°C  (high = +70.0°C, crit = +100.0°C)  

danne@danne-laptop:~$ 

```

---

