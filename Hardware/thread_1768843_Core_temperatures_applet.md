---
title: "Core temperatures applet"
date: 2011-05-27
forum: Hardware
---

### Post by gameguy on 2011-05-27
I am running ubuntu (desktop edition) on an old laptop of mine. It is running as a server but since I had always found that in windows it would be running hot, I wanted to check the CPU temperature under linux using a gnome applet (or something I can easily see all the time). I have disabled unity. I have a core 2 duo CPU, if it helps.
I have tried all this stuff (sorry that it's so big)

server@Server-NB:~$ sudo apt-get install lm-sensors
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
server@Server-NB:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 98.7 kB of archives.
After this operation, 475 kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/universe lm-sensors amd64 1:3.2.0-1ubuntu1 [98.7 kB]
Fetched 98.7 kB in 0s (320 kB/s)    
Selecting previously deselected package lm-sensors.
(Reading database ... 129688 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a3.2.0-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up lm-sensors (1:3.2.0-1ubuntu1) ...
server@Server-NB:~$ sudo sensors-detect
# sensors-detect revision 5861 (2010-09-21 17:21:05 +0200)
# System: TOSHIBA Satellite A500 (laptop)
# Board: TOSHIBA KSKAA

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): Yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
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
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: YUAN High-Tech MC770 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Adapter cannot be probed, skipping.
Next adapter: DiBX000 tuner I2C bus (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Adapter cannot be probed, skipping.
Next adapter: Radeon i2c bit bus 0x90 (i2c-2)
Do you want to scan it? (YES/no/selectively): y
y

Next adapter: Radeon i2c bit bus 0x91 (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Next adapter: Radeon i2c bit bus 0x92 (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus 0x93 (i2c-5)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus 0x94 (i2c-6)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus 0x95 (i2c-7)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Radeon i2c bit bus 0x96 (i2c-8)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: Radeon aux bus DP-auxch (i2c-9)
Do you want to scan it? (YES/no/selectively): y

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

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
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

server@Server-NB:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
server@Server-NB:~$ sudo apt-get install libsensors3 sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hddtemp libsensors-applet-plugin0
Suggested packages:
  ksensors
The following NEW packages will be installed:
  hddtemp libsensors-applet-plugin0 libsensors3 sensors-applet
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 320 kB of archives.
After this operation, 1,679 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/universe libsensors-applet-plugin0 amd64 2.2.7-2ubuntu2 [13.9 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/universe libsensors3 amd64 1:2.10.8-2 [130 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/universe sensors-applet amd64 2.2.7-2ubuntu2 [120 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/universe hddtemp amd64 0.3-beta15-46 [56.4 kB]
Fetched 320 kB in 2s (121 kB/s)    
Preconfiguring packages ...
Selecting previously deselected package libsensors-applet-plugin0.
(Reading database ... 129725 files and directories currently installed.)
Unpacking libsensors-applet-plugin0 (from .../libsensors-applet-plugin0_2.2.7-2ubuntu2_amd64.deb) ...
Selecting previously deselected package libsensors3.
Unpacking libsensors3 (from .../libsensors3_1%3a2.10.8-2_amd64.deb) ...
Selecting previously deselected package sensors-applet.
Unpacking sensors-applet (from .../sensors-applet_2.2.7-2ubuntu2_amd64.deb) ...
Selecting previously deselected package hddtemp.
Unpacking hddtemp (from .../hddtemp_0.3-beta15-46_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up libsensors-applet-plugin0 (2.2.7-2ubuntu2) ...
Setting up libsensors3 (1:2.10.8-2) ...

Creating config file /etc/sensors.conf with new version
Setting up sensors-applet (2.2.7-2ubuntu2) ...
Setting up hddtemp (0.3-beta15-46) ...
 * Starting disk temperature monitoring daemon hddtemp:                                                                                                          [ OK ] 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
server@Server-NB:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
server@Server-NB:~$ sudo apt-get install computertemp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-gnomeapplet
The following NEW packages will be installed:
  computertemp python-gnomeapplet
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 68.8 kB of archives.
After this operation, 618 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/main python-gnomeapplet amd64 2.32.0-0ubuntu2 [19.8 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty/universe computertemp all 0.9.6.1-1.1 [49.1 kB]
Fetched 68.8 kB in 1s (51.4 kB/s)       
Selecting previously deselected package python-gnomeapplet.
(Reading database ... 129827 files and directories currently installed.)
Unpacking python-gnomeapplet (from .../python-gnomeapplet_2.32.0-0ubuntu2_amd64.deb) ...
Selecting previously deselected package computertemp.
Unpacking computertemp (from .../computertemp_0.9.6.1-1.1_all.deb) ...
Processing triggers for gconf2 ...
Setting up python-gnomeapplet (2.32.0-0ubuntu2) ...
Setting up computertemp (0.9.6.1-1.1) ...
Processing triggers for python-support ...
server@Server-NB:~$ computertemp
computertemp: command not found
server@Server-NB:~$ cat /proc/acpi/thermal_zone/THRM/temperature
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
server@Server-NB:~$

---

