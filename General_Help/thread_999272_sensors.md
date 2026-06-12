---
title: "sensors"
date: 2008-12-01
forum: General Help
---

### Post by jcoolkatzerg on 2008-12-01
I have been working on an older sony vaio laptop (model #PCG-GR300P), and it gets really hot on the bottom.  Recently, some time after upgrading the machine to Intrepid, I have been having random shutdowns.  I believe this is heat-related, because this occurs even in the CMOS screens.  The fan built into the machine has never worked under Ubuntu, however, under WinXP, it did.  I have been trying to find a solution for this, and have not.  I have tried reinstalling lm-sensors, run sensors-detect, and I haven't found a solution.  Here are some outputs to ponder:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +47.9°C  (crit = +99.9°C
```
```
$ sudo sensors-detect
[sudo] password for jeremy: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801CA/CAM ICH3

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
yModule loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1880 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
    (note: this is probably NOT a sensor chip!)

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
Found `SMSC LPC47N227 Super IO'                             
    (no hardware monitoring capabilities)
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
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

Any suggestions?  I'm really at a loss here of what to do.

---

### Post by fragos on 2008-12-02
Perhaps on that vintage of Sony laptop the interface to sensors is proprietary and Sony created drivers for Windows. I tried googling ("PCG-GR300P"+sensors) and got a few hits. Perhaps that can help you.

---

### Post by jcoolkatzerg on 2008-12-04
I'll check into that and get back to you.

---

### Post by frankleeee on 2008-12-04
You might try sensors applet in synaptic which is a applet that goes to add to panel and see if it is reading any sensors that are working. Otherwise there are a lot of sensors stuff in synaptic you may just have to search and see what will be read by the applet.

---

### Post by jcoolkatzerg on 2008-12-05
The google search returned very little of use.  However, the sensors-applet has come back with something interesting...it seems to be pulling a temp from acpi, which is mirrored by libsensors.  There is nothing else, though.

---

### Post by Nathan Sweeney on 2008-12-05
In the bios can you set the fans to run at all times?  On my HP, the fans were set by default to run all the time, at a low speed, then they throttle up when the heat gets up there.

---

### Post by fragos on 2008-12-05
Older PCs were very inconsistent with power control and not well supported by Linux. If I'm not mistaken ACPI may not be newer vintage than your PC was designed for. We're getting into foggier areas of my knowledge so I can't speak with authority on this issue.

---

### Post by frankleeee on 2008-12-05
> **jcoolkatzerg said:**
> The google search returned very little of use.  However, the sensors-applet has come back with something interesting...it seems to be pulling a temp from acpi, which is mirrored by libsensors.  There is nothing else, though.

Have you tried installing the lm-sensors or any others in synaptic.
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
I looked hard for answers, this is the closest I think that might be worth looking at.

---

### Post by dcstar on 2008-12-05
> **jcoolkatzerg said:**
> I have been working on an older sony vaio laptop (model #PCG-GR300P), and it gets really hot on the bottom.  Recently, some time after upgrading the machine to Intrepid, I have been having random shutdowns.
..........
Any suggestions?  I'm really at a loss here of what to do.

You may want to check if the current Linux kernel supports the type of on-board sensors/ACPI that you have. You may be able to compile your own kernel with it enabled if it is available.

Prior to 8.04, my on-board sensors didn't function because the kernels prior to that version did not support my motherboard.

---

### Post by jcoolkatzerg on 2008-12-06
> **Nathan Sweeney said:**
> In the bios can you set the fans to run at all times?  On my HP, the fans were set by default to run all the time, at a low speed, then they throttle up when the heat gets up there.

There isn't an option for this in the bios. I've tried to see if there is someway to write a value to the fan from ubuntu, but I can't even find the fan!

> **fragos said:**
> Older PCs were very inconsistent with power control and not well supported by Linux. If I'm not mistaken ACPI may not be newer vintage than your PC was designed for. We're getting into foggier areas of my knowledge so I can't speak with authority on this issue.

ACPI is working fine, I beleve.  I just don't think it sees my sensors outside of the one on board the cpu.  Standby and everything else work ok.

> **frankleeee said:**
> Have you tried installing the lm-sensors or any others in synaptic.
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
I looked hard for answers, this is the closest I think that might be worth looking at.

lm-sensors doesn't see anything.  I had it installed before and just tried reinstalling.  Still nothing, even after re-running sensors-detect.

> **dcstar said:**
> You may want to check if the current Linux kernel supports the type of on-board sensors/ACPI that you have. You may be able to compile your own kernel with it enabled if it is available.

Prior to 8.04, my on-board sensors didn't function because the kernels prior to that version did not support my motherboard.

Interesting.....I have the latest kernels installed from the 8.10 repositories, however, I haven't tried compiling it on my own.  If it comes down to that, I'm also going to try to compile a way to undervolt the CPU.  That will help with heat, even if I never get the sensors/fan to work. [http://ubuntuforums.org/showthread.php?t=786402]("http://ubuntuforums.org/showthread.php?t=786402").  I'd rather avoid messing with my kernel for a few more weeks, at least until after finals.

---

