---
title: "CPU Temp really high! is fan working properly?"
date: 2010-09-22
forum: Hardware
---

### Post by fuzzylogic25 on 2010-09-22
I have a Intel Core 2 Duo 1.86ghz and each core is at 60-63C. Under windows it was never getting past 48C.

The fan is very quite and I feel it should increase its speed now that it is that hot. How do you control fan speeds in Ubuntu?

---

### Post by tadaskr on 2010-09-22
When temperature gets hot restart computer then bios speed up fans and in ubuntu it will work how bios set

---

### Post by Dex73 on 2010-09-24
I have issues with fan speed but my bios menu doesn't have any fan settings. Is their another way? Perhaps some program I can install?

---

### Post by sikander3786 on 2010-09-24
Most of the newer motherboard Bios have temperature sensor and fan speed controls built-in. See if you also have one.

You can also use lm-sensors. See a guide here.

[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

And also here.

[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

---

### Post by Dex73 on 2010-09-24
> **sikander3786 said:**
> Most of the newer motherboard Bios have temperature sensor and fan speed controls built-in. See if you also have one.

You can also use lm-sensors. See a guide here.

[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

And also here.

[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

I don't think I have one. Nothing in BIOS and I tried you first link. Here is my output...

$ sudo pwmconfig
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


The second link doesn't seem to be about fans at all. No biggy. My computer is below critical temp.

---

### Post by sikander3786 on 2010-09-24
The second link is also about fan speeds. Title **"HOWTO Control Fan Speed"**.

You need to install the modules before you can control the fan speed.

>     * More info on how to detect CPU temperatures, [fan speeds and voltages using lm-sensors.]("http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu")
    * Install and config lm-sensors first as given in the link above. Then run pwmconfig to test your fans


Did you do that before running pwmmconfig?

I haven't seen any easy to use tool like in Windows, just double click and install and use on Linux. A bit of hard work is required. May be not worth if you don't have any problems with temperatures.

---

### Post by Dex73 on 2010-09-24
Sorry, I've reread it and you are undoubtedly write. As for lm-sensors, I have them installed, even tried to reinstall them and got this...

$ sudo apt-get install lm-sensors
[sudo] password for next: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

then typed pwmmconfig and got the message from the previous post. I plan to not worry about it until it becomes a problem. Thanks for all the help.

---

### Post by jcolyn on 2010-09-24
For lm-sensors to properly work you have to run ```
sudo sensors-detect
``` at the terminal and answer yes to all of the questions.. Once done then you can setup fan control etc..

---

### Post by Dex73 on 2010-09-24
> **jcolyn said:**
> For lm-sensors to properly work you have to run ```
sudo sensors-detect
``` at the terminal and answer yes to all of the questions.. Once done then you can setup fan control etc..

Did this...

$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Gateway MT6840

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
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87591 Super IO'                         
    (address 0x200, but not activated)
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
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK               

next@one-laptop:~$ pwmconfig
You need to be root to run this script.
next@one-laptop:~$ sudo pwmconfig
[sudo] password for next: 
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

Then I typed sensors just to see.

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +86.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (crit = +85.0°C)  

Are these the right commands to a least go on with the tutorial? Shouldn't I be able to detect them? I want to be sure before I move on.

---

### Post by pyrforos on 2011-01-28
i have the exact same problem with a vaio vgn-fz21 .PLEASE  help!
I HAVE to speed up the fan or my GPU dies... I had to reheat the soldering paste 2 times..

---

