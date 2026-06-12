---
title: "Help with sensors-detect on my Laptop."
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by qingliu on 2006-04-02
](*,) I installed Sensor already. However, I guess it cannnot detecy my hardware. 

My Laptop: PM 750, 
1 GB
80GB 
ATI X 600 VIDEO CARD, CHIP ID :0X3105


qingliu@qingliu:~$ sudo sensors-detect

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
You do not need any special privileges for this.
Do you want to probe now? (YES/no): YeS
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 00:1f.3: Intel 82801FB ICH6
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

We are now going to do the adapter probings. Some adapters may hang halfway
through; we can't really help that. Also, some chips will be double detected;
we choose the one with the highest confidence value in that case.
If you found that the adapter hung after probing a certain address, you can
specify that address to remain unprobed. That often
includes address 0x69 (clock chip).

Next adapter: SMBus I801 adapter at 20a0
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x08
Client found at address 0x31
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'... Failed!
Client at address 0x50 can not be probed - unload all client drivers first!
Client at address 0x51 can not be probed - unload all client drivers first!
Client found at address 0x69

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): YES
Probing for `National Semiconductor LM78'
Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
Trying general detect... Failed!
Probing for `ITE IT8712F'
Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for `ITE 8702F Super IO Sensors'
Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
Failed! (skipping family)
Probing for `Winbond W83627EHF Super IO Sensors'
Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): YES
Probing for `ITE 8702F Super IO Sensors'
Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
Failed! (skipping family)
Probing for `Winbond W83627EHF Super IO Sensors'
Failed! (skipping family)

Sorry, no chips were detected.
Either your sensors are not supported, or they are
connected to an I2C bus adapter that we do not support.
See doc/FAQ, doc/lm_sensors-FAQ.html, or
[http://www2.lm-sensors.nu/~lm78/cvs...ensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs...ensors-FAQ.html)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, see
[http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.
qingliu@qingliu:~$

Here is the list or output. 

Please help me take a look, thanks

---

