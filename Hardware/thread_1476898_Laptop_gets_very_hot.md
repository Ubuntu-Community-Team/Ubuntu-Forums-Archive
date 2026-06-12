---
title: "Laptop gets very hot"
date: 2010-05-08
forum: Hardware
---

### Post by imiunleashed on 2010-05-08
Hey guys i have got HP dv6 2.13 core 2 duo, 3 gb ram and ATI Radeon Mobility 512 VGA.
Lately i figured out that using Ubuntu 10.04 makes the laptop very hot ( this is the first time i use Ubuntu).
Could someone please help me on this...

---

### Post by dlradlt on 2010-05-08
Ubuntu shouldn't make your laptop run hot check your cooling fan to make sure that its not dirty and that the heat sinks cooling fins are open to air flow with a can of compressed air 

just spray the air or blow through the vent holes where the hot air comes out with the laptop off and that should do the trick you should be able to see the cooling fan spin and a bunch of dust should come out   

Do you have something else to compare your conclusion with like are you dual booting with windows and Ubuntu and not having the heat problem in windows 


you could try a slightly older version of ubuntu like 9.10 or 9.04lts sometime bug's will get released in newer bleeding edge releases of Linux that need time to get ironed out 

also there are some closed source video drivers that have issues so check the hardware compatibilty at [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by Jimtheplanner on 2010-05-09
Hi Guy's,

I've had issues also with my Dell 1545:-

You can try adding in sensors via the terminal

```
sudo apt-get install lm-sensors sensors-applet hddtemp
sudo apt-get install cpufrequtils lm-sensors
```

First for your hard drive second for CPU frequency, then
```

sudo sensors-detect 
```

Say **_yes_** to all questions, then check your temps using the following command.

```
sensors
```

I still had issues with video flicker etc and decided to revert back to Mandriva where things run as cool as a cucumber.....

Jim

---

### Post by imiunleashed on 2010-05-09
> **Jimtheplanner said:**
> Hi Guy's,

I've had issues also with my Dell 1545:-

You can try adding in sensors via the terminal

```
sudo apt-get install lm-sensors sensors-applet hddtemp
sudo apt-get install cpufrequtils lm-sensors
```

First for your hard drive second for CPU frequency, then
```

sudo sensors-detect 
```

Say **_yes_** to all questions, then check your temps using the following command.

```
sensors
```

I still had issues with video flicker etc and decided to revert back to Mandriva where things run as cool as a cucumber.....

Jim

Tried this Jim,when i start sensors all i get is:

> No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.


I have installed Ubuntu inside Microsoft Windows, could that be the reason?

Also this problem has been specific to Ubuntu, Vista works fine and does not let my laptop get hot..:)
So dlradlt that could not be the prob, also the link you have given does not work :(

---

### Post by Jimtheplanner on 2010-05-09
Ok

This is what I get for:-

 ```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

> james@Inspiron:~$ sudo apt-get install lm-sensors sensors-applet hddtemp
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsensors-applet-plugin0
Suggested packages:
  ksensors
The following NEW packages will be installed
  hddtemp libsensors-applet-plugin0 sensors-applet
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 183kB of archives.
After this operation, 1,085kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe libsensors-applet-plugin0 2.2.3-2ubuntu1 [19.2kB]
Get: 2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe sensors-applet 2.2.3-2ubuntu1 [107kB]
Get: 3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe hddtemp 0.3-beta15-45 [56.3kB]
Fetched 183kB in 0s (218kB/s)
Preconfiguring packages ...
Selecting previously deselected package libsensors-applet-plugin0.
(Reading database ... 143610 files and directories currently installed.)
Unpacking libsensors-applet-plugin0 (from .../libsensors-applet-plugin0_2.2.3-2ubuntu1_amd64.deb) ...
Selecting previously deselected package sensors-applet.
Unpacking sensors-applet (from .../sensors-applet_2.2.3-2ubuntu1_amd64.deb) ...
Selecting previously deselected package hddtemp.
Unpacking hddtemp (from .../hddtemp_0.3-beta15-45_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up libsensors-applet-plugin0 (2.2.3-2ubuntu1) ...

Setting up sensors-applet (2.2.3-2ubuntu1) ...

Setting up hddtemp (0.3-beta15-45) ...
 * Starting disk temperature monitoring daemon hddtemp:                  [ OK ] 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

And for:-

```
sudo apt-get install cpufrequtils lm-sensors  
```

> james@Inspiron:~$ sudo apt-get install cpufrequtils lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcpufreq0
The following NEW packages will be installed
  cpufrequtils libcpufreq0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.

And to Kick it all off I do:-

```
sudo sensors-detect
```

> james@Inspiron:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Dell Inc. Inspiron 1545
# Board: Dell Inc. 0G848F

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
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11

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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9
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

Next adapter: DPDDC-D (i2c-2)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: SMBus I801 adapter at 1100 (i2c-3)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
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

And to check:

```
sensors

```
> james@Inspiron:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.5°C  (crit = +100.0°C)                  

james@Inspiron:~$ 

Hope this helps....

Jim

---

### Post by dlradlt on 2010-05-09
> **imiunleashed said:**
> Tried this Jim,when i start sensors all i get is:



I have installed Ubuntu inside Microsoft Windows, could that be the reason?

Also this problem has been specific to Ubuntu, Vista works fine and does not let my laptop get hot..:)
So dlradlt that could not be the prob, also the link you have given does not work :(
that link worked when i reply to your post it not work for me either right now web server not responding ???

installed in windows ?? how virtual machine wubi ????

I'd still try a older version of linux like 9.10 

10.04 hasn't been released for a month so its likely to have bugs.

I also had some heat issues crashed my laptop twice but I was playing smokein guns under 10.04 after i upgraded from 9.10 and I assumed it was a video issue so i just reinstalled 9.10 and the heat and Video problem went away.

I'm running a Toshiba Satellite L355-7905 2.2ghz Celron 3gb ram Intel 4500gma

it looks like there's a common problem but I'm not sure what it is and I'm not about to reinstall or upgrade until this bug has been worked out. 

I wonder if I'll have the same problem running 10.04 from my flash drive I'll try it and update you guys later

---

### Post by PyrexKidd on 2010-05-09
> 
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.


I'm having the same problem.  Except when I run:
```

sudo sensors-detect

```
this is the only one that is a success.  all others are no
```

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')

```

when I installed it the HDD configure script asked if I wanted to load drivers at boot.  and I could go back and change it using a command.

I dumbly forgot to write down that command and now I want to turn the drivers off on boot.  how do I do that?  

I was going to try:
```

sudo apt-get remove sensors-applet hddtemp
sudo apt-get remove cpufrequtils

```
since lm-sensors was installed from the box
any thoughts?


oh and the whole reason I started reading this thread:
I am having a similar problem with mine getting very hot.
I'm using an HP Pavilon dv6-2180
AMD Turion(tm) II Ultra Dual-Core Mobile M620
6GB ram
ATI Mobility Radeon HD 4650 w/ 1024 MB of RAM

it is a brand new laptop, I just picked it up about a month ago, I cleaned out the fan anyway and it still seems to run hot.  It seems to run hotter on AC power than on battery power.  I have a dual boot setup w/ windows 7 (I think I've booted windows five times in the month I've owned it...) and it doesn't run as hot in windows.

---

### Post by imiunleashed on 2010-05-14
yeah i installed via wubi :)
Still no luck, sensors do not seem to work, i am trying to reinstall and see, else bye bye Ubuntu :(

---

