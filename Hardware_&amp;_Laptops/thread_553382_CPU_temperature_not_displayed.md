---
title: "CPU temperature not displayed"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by Llewellyn01 on 2007-09-17
Hi there,

I am running Feisty Fawn on a Fujitsu Lifebook T3010 and for the life of me I cannot get the lm sensors to work to let me know what the CPU temperature is, I have tried the guides but to no effect.

On the off chance does anyone know how to get them working or am I just missing something in my frustration? I am doing my best to learn about Ubuntu but on this occasion I could do with some help.

Many Thanks if you can help?

Cheers

Rich

---

### Post by w4ett on 2007-09-17
did you run it like this:

```
sudo sensors-detect
```

---

### Post by Llewellyn01 on 2007-09-18
> **w4ett said:**
> did you run it like this:

```
sudo sensors-detect
```

Yes, but it never picked up the CPU.

Here is a copy and paste of the results:

richard@TARDIS:~$ sudo sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801DB ICH4

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1860
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x09
Probing for `Smart Battery Charger'...                      Success!
    (confidence 5, driver `to-be-written')
Client found at address 0x0a
Probing for `Smart Battery Manager/Selector'...             Success!
    (confidence 5, driver `to-be-written')
Client found at address 0x0b
Probing for `Smart Battery'...                              Success!
    (confidence 5, driver `smartbatt')
Client found at address 0x19
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Philips Semiconductors PCA9556'...             No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 1860'
    Busdriver `i2c-i801', I2C address 0x09
    Chip `Smart Battery Charger' (confidence: 5)
  * Bus `SMBus I801 adapter at 1860'
    Busdriver `i2c-i801', I2C address 0x0a
    Chip `Smart Battery Manager/Selector' (confidence: 5)

Driver `smartbatt' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 1860'
    Busdriver `i2c-i801', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
# no driver for Smart Battery Charger yet
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)yes

---

### Post by w4ett on 2007-09-18
I've done some searching for you and have seen some problems with your brand laptop in correctly detecting the temps.

IMO, I would go to: [http://lm-sensors.org/](http://lm-sensors.org/) and post on their forum with your particular problem.

Good Luck

---

