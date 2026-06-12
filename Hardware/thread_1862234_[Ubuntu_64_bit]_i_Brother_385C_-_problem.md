---
title: "[Ubuntu 64 bit] i Brother 385C - problem"
date: 2011-10-16
forum: Hardware
---

### Post by r411 on 2011-10-16
Hello

I apologize for my language, but do not know how well the English 
and translated by google translate everything - the Polish forums 
could not help me can you help me .. Gentlemen

recently installed Ubuntu Linux 64 bit 10.04.
Before someone writes something on the internet looking for a solution to your
problem, but resulted in no solution.
I am new to linux, student it all the time -
Please bear with us.

The command uname-a returns:
```
  daniel88 Linux 6.2.38-11-generic # 50-Ubuntu SMP Mon Sep 12 9:17:25 p.m.
UTC 2011 x86_64 x86_64 x86_64 GNU / Linux 
```When you turn the printer on sytem it detects the wizard searches for the driver but not
can find the database.

I downloaded the appropriate driver. Deb.
I installed using:
```
  sudo dpkg-i - force-architecture
'/ Home/daniel/Pulpit/dcp385clpr-1.1.2-2.i386.deb' 
```returned the message:

```

dpkg: warning: Ignoring a problem when you use the - force:
 package architecture (i386) does not agree with the system architecture
 (Amd64)
(Reading database ... 213758 files and directories currently
installed.)
Preparing to replace dcp385clpr: i386 1.1.2-2 (using
.../dcp385clpr-1.1.2-2.i386.deb) ...
Unpacking replacement dcp385clpr: i386 ...
Configuring dcp385clpr: i386 (1.1.2-2) ...
```Then:

```
sudo dpkg-i - force-architecture
'/ Home/daniel/Pulpit/dcp385ccupswrapper-1.1.2-2.i386.deb' 
```returned the message:

 ```
package architecture (i386) does not agree with the system architecture
 (Amd64)
(Reading database ... 213758 files and directories currently
installed.)
Preparing to replace dcp385ccupswrapper: i386 1.1.2-2
(Using .../dcp385ccupswrapper-1.1.2-2.i386.deb) ...
cups stop / waiting
cups start / running, process 2785
Unpacking replacement dcp385ccupswrapper: i386 ...
Configuring dcp385ccupswrapper: i386 (1.1.2-2) ...
cups stop / waiting
cups start / running, process 2862
```I set as the default printer

I downloaded the printer driver from the
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)

Then:

```
sudo dpkg-i brscan3-0.2.11-4.amd64.deb 
```returned the message:

```
Selecting previously deselected package brscan3.
(Reading database ... 213758 files and directories currently
installed.)
Unpacking brscan3 (with brscan3-0.2.11-4.amd64.deb) ...
Configuring brscan3 (0.2.11-4) ...
```Then:

```
sudo gedit / lib/udev/rules.d/40-libsane.rules 
```and added entry:

```
# Brother scanners
Attrs {idVendor} == "04f9", ENV {libsane_matched} = "yes"

# The Following rule will disable the USB autosuspend for the device
ENV {libsane_matched} == "yes", RUN + = "/ bin / sh-c 'test-e
/ Sys / $ env {DEVPATH} / power / level & & echo on>
/ Sys / $ env {DEVPATH} / power / level '"
LABEL = "libsane_rules_end"
```lsusb returns to me:

```
Bus 008 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04f9: 0201 Brother Industries, Ltd
Bus 005 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub 
```When trying to print is at this stage:
 
[IMG]http://images39.fotosik.pl/1117/a56276f5fe6a0729.jpg[/IMG]

Just to be sure installed:
```
sudo dpkg-i brscan-skey-0.2.1-3.amd64.deb 
```returned the message:

[HTML]Selecting previously deselected package brscan-skey.
(Reading database ... 213776 files and directories currently
installed.)
Unpacking brscan-skey (from brscan-skey-0.2.1-3.amd64.deb) ...
Configuring brscan-skey (0.2.1-3).[/HTML]scanner can not connect to the computer - turn on the printer when the system
does not display a lack of driver ...
What did I do wrong ?????? help
Does anyone managed to install the driver on ubunciaku?
Please help and guidance ....
Thanks in advance for your help ......

I hope you understood what I meant - please help - thanks

---

