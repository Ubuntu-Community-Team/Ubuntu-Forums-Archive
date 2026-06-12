---
title: "Fan Speed"
date: 2013-02-15
forum: Hardware
---

### Post by Articcu on 2013-02-15
Hello!

I only just installed Ubuntu, and it is the first Linux I've use. I have it alongside with Windows.

Computer specs: i7 @3.40ghz x8, 8GB Ram, AMD HD Radeon 6870

The issue is that the fans sound like they're running at full speed constantly. I tried a few fixed, but none of them have worked. I have no idea what to do, and the sound is rather annoying, and probably will make my fans last for a shorter period of time as well. In windows the fans seem to adjust according to the load of what I'm doing, IE while browsing you barely hear the fans, but now they're constantly full speed.

Would appreciate any help!

---

### Post by Dodeca on 2013-02-15
Is your computer a LAPTOP ... my laptop did the same. Suggest you search for a way to monitor cpu temp and a way to throttle down the cpu when needed.

---

### Post by Articcu on 2013-02-15
Not a laptop! Usin 12.04, btw

---

### Post by Yellow Pasque on 2013-02-15
If the fans are running full speed, the first thing you need to do is check your temps and determine whether the fans are running full speed because they need to:
```
sudo apt-get install fancontrol lm-sensors i2c-tools
sudo sensors-detect #answer 'y' to the prompts
sensors
```
Post output of sensors if you don't understand it.

The next thing I'd do is check BIOS to make sure fan control's on, and after that, I would check for BIOS updates. If the BIOS fan control still isn't behaving correctly, I would turn it off and play with the fancontrol scripts:
```
sudo pwmconfig
sudo fancontrol
```

Note that if you decide to keep the BIOS fan control off, you'll need a software fan control for Windows (SpeedFan comes to mind).

---

### Post by beholder88 on 2013-04-23
I too am having the same issue, I did what was advised earlier and here is what I got:
(By the way I have a Hewlett-Packard HP Pavilion dv5 (laptop))

eric@RED:~$ sudo apt-get install fancontrol lm-sensors i2c-tools
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fancontrol is already the newest version.
lm-sensors is already the newest version.
Suggested packages:
  libi2c-dev python-smbus
The following NEW packages will be installed:
  i2c-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.7kB of archives.
After this operation, 266kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe i2c-tools 3.0.2-4 [53.7kB]
Fetched 53.7kB in 0s (236kB/s)     
Selecting previously deselected package i2c-tools.
(Reading database ... 146001 files and directories currently installed.)
Unpacking i2c-tools (from .../i2c-tools_3.0.2-4_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up i2c-tools (3.0.2-4) ...


eric@RED:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Hewlett-Packard HP Pavilion dv5 Notebook PC (laptop)
# Board: Hewlett-Packard 144E


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
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8500
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


Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)


Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.


No modules to load, skipping modules configuration.


Unloading i2c-dev... OK

---

### Post by Yellow Pasque on 2013-04-24
Laptops control their fan through ACPI, so my earlier post in this thread is irrelevant to laptops.

---

