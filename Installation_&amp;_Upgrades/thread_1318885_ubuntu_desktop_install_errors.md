---
title: "ubuntu desktop install errors"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by GamingJunkie on 2009-11-08
Hi, I'm getting some errors installing ubuntu desktop, I hope someone can help me, already checked google, a lot of talk but I couldn't find any fix which worked for me:

> :~# sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  acpi acpi-support acpid powermanagement-interface
The following NEW packages will be installed
  acpi acpi-support acpid powermanagement-interface ubuntu-desktop
0 upgraded, 5 newly installed, 0 to remove and 105 not upgraded.
Need to get 0B/118kB of archives.
After this operation, 1315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package acpi.
(Reading database ... 120282 files and directories currently installed.)
Unpacking acpi (from .../acpi_0.09-3ubuntu1_i386.deb) ...
Selecting previously deselected package acpid.
Unpacking acpid (from .../acpid_1.0.4-5ubuntu9.3_i386.deb) ...
Selecting previously deselected package acpi-support.
Unpacking acpi-support (from .../acpi-support_0.109-0hardy2_i386.deb) ...
Selecting previously deselected package powermanagement-interface.
Unpacking powermanagement-interface (from .../powermanagement-interface_0.3.18_i386.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.102_i386.deb) ...
Setting up acpi (0.09-3ubuntu1) ...
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                                                                                                 acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)I'm new to Linux/Ubuntu by the way;)

---

