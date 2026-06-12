---
title: "Toshiba: Trying to set fan to full speed."
date: 2013-10-16
forum: Hardware
---

### Post by Piro ko on 2013-10-16
Here's the brief of it.
I need to set the fan of my laptop to run at full speed when I want.

The less brief is this:
My laptop is old, and I use lm_sensors to keep tabs on CPU temperature as on rare occasion the computer overheats.
The model of the laptop is Toshiba Satellite A205-s4597
The fan runs, and adjusts itself automatically without too much trouble, however I'd like to just set it to "100% power" when I'm doing anything processor intensive to ensure it is far less likely to overheat and crash because rarely the fan does NOT rev up all the way before it's too late.
I can't control my fan speed so far as I have tried.
I've installed lm_sensors and when I run the command "sensors" in the terminal it gives me temperature sensors, but no fan speed.
If lm_sensors doesn't detect fan speed, is there any other way to control it?
Clearly the fan is there, and it works. Worst case scenario I dont mind using a script that will set the fan to 100% speed at all times.

I'm fairly tech savy but I'm new to command line so please spell things out.
-piroko

---

### Post by Piro ko on 2013-10-18
Finally found some information that's related. Using the suggestions on this thread to help lm_sensors see my fan:
[http://ubuntuforums.org/showthread.php?t=1192519](http://ubuntuforums.org/showthread.php?t=1192519)

the command

```
sudo modprobe w83627ehf force_id=0x8860
```

brought up the rest of the sensors.
When using lm_sensors before, all I got was core temps.

In order to make this permanent so that lm_sensors would always show the rest of the information, I opened terminal
and put:

 ```
sudo gedit /etc/modules
```

Then I went to the bottom of the file and typed in a new line saying:

```
w83627ehf force_id=0x8860
```

Now "sensors" command from terminal gives me 3 fan sensors that read 0.
It's only at this point that I realize I've likely used a command for a chip I don't have.
So I've gone back and removed the "w83627..." line from the /etc/modules.
Now what?

---

### Post by Piro ko on 2013-10-18
For reference, this is my sensors output:

```

andrew@Andrews-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +63.0°C  (crit = +106.0°C)                  
temp2:       +58.0°C  (crit = +91.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +58.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (crit = +85.0°C)                  

andrew@Andrews-laptop:~$
```

And sensors-detect shows this:

```
andrew@Andrews-laptop:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: TOSHIBA Satellite A205
# Board: Intel Corporation CAPELL VALLEY(NAPA) CRB

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
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
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
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
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): yes
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

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK

andrew@Andrews-laptop:~$ 


```

---

### Post by Piro ko on 2013-10-18
My BIOS doesn't offer a fan option.
So there's one more route examined.

---

### Post by Piro ko on 2013-10-30
The lesson here kids, is this:
If you buy a laptop model that isn't super common, dont expect an easy solution 5 years down the road to hardware quirks. Because other people won't have figured it out, and other people wont necessarily have the same hardware components meaning fixes specific to your computer aren't so likely to come around.
Calling this thread dead for now.

-Piro ko

---

