---
title: "Power manager stopped working"
date: 2012-02-12
forum: Hardware
---

### Post by ztMAMOHT on 2012-02-12
System Settings-->Power Management. Get this: 
```

Power Management configuration module could not be loaded. 
The Power Management Service appears not to be running. 
This can be solved by starting or scheduling it inside "Startup and Shutdown"

```

System Settings-->Startup and Shutdown-->Service Manager.
Power Management have status: "Running"
When I try to stop no Error.
When I try to start:
```

KDE Power Management System could not be initialized. The backend reported the following
error: No valid Power Management backend plugins are available. A new installation
might solve this problem. Please check your system configuration.

```
Few days ago every was fine.

---

### Post by timrichardson on 2012-02-13
Same problem for me after latest 4.8.0 packages were installed (some packages have 4.8.0a version now).
Shortly afterwards I received a new kernel, but the power management breakage happened before the new kernel and was not fixed by the new kernel.

---

### Post by ztMAMOHT on 2012-02-14
Can I some how reinstall power manager?

---

### Post by ThomasAndersn on 2012-02-15
Well, U need to install PowerTOP. To install run the command:

sudo apt-get install powertop


you must running from battery power for powertop to get machine's current watt uasage.
After install, run the following to pm-utils package for managing low power modes:
sudo aptitude install pm-utils
To run in low power mode:
sudo pm-powersave true
To leave low power mode:
sudo pm-powersave false

---

### Post by ztMAMOHT on 2012-02-15
Have error:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpng12-dev libjpeg62-dev zlib1g-dev libfreetype6-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cpufrequtils ethtool hal hal-info laptop-mode-tools libcpufreq0 libhal-storage1 libhal1 libnl2 sdparm
Suggested packages:
  gnome-device-manager
The following NEW packages will be installed:
  cpufrequtils ethtool hal hal-info laptop-mode-tools libcpufreq0 libhal-storage1 libhal1 libnl2 powertop sdparm
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,160 kB of archives.
After this operation, 5,063 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libcpufreq0 cpufrequtils ethtool libhal1 libhal-storage1 hal-info hal laptop-mode-tools libnl2 sdparm powertop
Authentication warning overridden.
Get:1 http://ubuntu.org.ua/ubuntu/ oneiric/universe libcpufreq0 i386 007-1 [13.6 kB]
Get:2 http://ubuntu.org.ua/ubuntu/ oneiric/universe cpufrequtils i386 007-1 [38.3 kB]
Get:3 http://ubuntu.org.ua/ubuntu/ oneiric/main ethtool i386 1:2.6.39-1 [87.6 kB]
Get:4 http://ubuntu.org.ua/ubuntu/ oneiric/universe libhal1 i386 0.5.14-6 [77.1 kB]
Get:5 http://ubuntu.org.ua/ubuntu/ oneiric/universe libhal-storage1 i386 0.5.14-6 [27.9 kB]
Get:6 http://ubuntu.org.ua/ubuntu/ oneiric/universe hal-info all 20091130-1 [47.4 kB]
Get:7 http://ubuntu.org.ua/ubuntu/ oneiric/universe hal i386 0.5.14-6 [372 kB]
Get:8 http://ubuntu.org.ua/ubuntu/ oneiric/universe laptop-mode-tools all 1.57-1ubuntu1 [101 kB]
Get:9 http://ubuntu.org.ua/ubuntu/ oneiric/main libnl2 i386 2.0-1 [163 kB]
Get:10 http://ubuntu.org.ua/ubuntu/ oneiric/universe sdparm i386 1.06-3 [106 kB]
Get:11 http://ubuntu.org.ua/ubuntu/ oneiric/main powertop i386 1.97-2 [125 kB]
Fetched 1,160 kB in 3s (348 kB/s)  
Preconfiguring packages ...
Selecting previously deselected package libcpufreq0.
(Reading database ... 300990 files and directories currently installed.)
Unpacking libcpufreq0 (from .../libcpufreq0_007-1_i386.deb) ...
Selecting previously deselected package cpufrequtils.
Unpacking cpufrequtils (from .../cpufrequtils_007-1_i386.deb) ...
Selecting previously deselected package ethtool.
Unpacking ethtool (from .../ethtool_1%3a2.6.39-1_i386.deb) ...                                                                                                                                  
Selecting previously deselected package libhal1.
Unpacking libhal1 (from .../libhal1_0.5.14-6_i386.deb) ...
Selecting previously deselected package libhal-storage1.
Unpacking libhal-storage1 (from .../libhal-storage1_0.5.14-6_i386.deb) ...
Selecting previously deselected package hal-info.
Unpacking hal-info (from .../hal-info_20091130-1_all.deb) ...
Selecting previously deselected package hal.
Unpacking hal (from .../archives/hal_0.5.14-6_i386.deb) ...
Selecting previously deselected package laptop-mode-tools.
Unpacking laptop-mode-tools (from .../laptop-mode-tools_1.57-1ubuntu1_all.deb) ...
Selecting previously deselected package libnl2.
Unpacking libnl2 (from .../archives/libnl2_2.0-1_i386.deb) ...
Selecting previously deselected package sdparm.
Unpacking sdparm (from .../sdparm_1.06-3_i386.deb) ...
Selecting previously deselected package powertop.
Unpacking powertop (from .../powertop_1.97-2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libcpufreq0 (007-1) ...
Setting up cpufrequtils (007-1) ...
 [COLOR="Red"]* Loading cpufreq kernel modules...                                                                                                                                                            FATAL: Error inserting e_powersaver (/lib/modules/3.0.0-15-generic/kernel/drivers/cpufreq/e_powersaver.ko): No such device
FATAL: Error inserting pcc_cpufreq (/lib/modules/3.0.0-15-generic/kernel/drivers/cpufreq/pcc-cpufreq.ko): No such device
FATAL: Error inserting p4_clockmod (/lib/modules/3.0.0-15-generic/kernel/drivers/cpufreq/p4-clockmod.ko): Device or resource busy[/COLOR]
                                                                                                                                                                                         [ OK ]
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                                                                                                                                       * CPU0...                                                                                                                                                                                       * CPU1...                                                                                                                                                                                       * CPU2...                                                                                                                                                                                       * CPU3...                                                                                                                                                                               [ OK ] 
Setting up ethtool (1:2.6.39-1) ...
Setting up libhal1 (0.5.14-6) ...
Setting up libhal-storage1 (0.5.14-6) ...
Setting up hal-info (20091130-1) ...
Setting up hal (0.5.14-6) ...
Setting up laptop-mode-tools (1.57-1ubuntu1) ...
 * Enabling laptop mode...                                                                                                                                                                      Unhandled kernel version: 3.0 ('uname -r' = '3.0.0-15-generic')
Couldn't acquire lock. Retrying....

Unhandled kernel version: 3.0 ('uname -r' = '3.0.0-15-generic')
                                                                                                                                                                                         [ OK ]
Setting up libnl2 (2.0-1) ...
Setting up sdparm (1.06-3) ...
Setting up powertop (1.97-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by ztMAMOHT on 2012-02-15
The problem is that I can't know how much battery charge remains.
Applet show: Not present.

---

### Post by ztMAMOHT on 2012-02-17
Problem solved. But I don't know exactly how:
[INDENT]1) may be installing upower(sudo apt-get install upower)[/INDENT]
[INDENT]2) and it is more likely. I plugin AC Adapter and pulled out/insert battery. Then restart.[/INDENT]

---

