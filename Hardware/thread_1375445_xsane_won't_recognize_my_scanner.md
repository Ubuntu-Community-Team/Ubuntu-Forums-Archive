---
title: "xsane won't recognize my scanner"
date: 2010-01-07
forum: Hardware
---

### Post by itachisxeyes on 2010-01-07
i already checked here: [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
its not listed so i'm not sure if its supported or not.
but i have a epson stylus photo rx595

anyone get it to work?

---

### Post by anglican on 2010-01-08
> **itachisxeyes said:**
> i already checked here: [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
its not listed so i'm not sure if its supported or not.
but i have a epson stylus photo rx595

anyone get it to work?

Epson linux support is pretty good. Go to:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

for printer and scanner software for your all-in-one.

H

---

### Post by Mzolk on 2010-03-20
> **itachisxeyes said:**
> i already checked here: [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
its not listed so i'm not sure if its supported or not.
but i have a epson stylus photo rx595

anyone get it to work?


Avasys didn't work for my system...but I found a solution and my rx595 is working with xsane in karmic.

1) In terminal type command 'lsusb' (without quotes) and look for the Epson name - for example the output on my terminal looked like this:

Bus 001 Device 005: ID 04b8:083c Seiko Epson Corp. MFP Composite Device

Note the ID numbers - 04b8:083c in my example - these are your **USB vendor ID:****USB product ID** codes

2) Go to /etc/sane.d/ and edit epkowa.conf (gedit /etc/sane.d/epkowa.conf) and look for the line that says:

#usb 0x04b8 0x0110

and beneath that type:

**usb 0x**(Enter your USB vendor ID code) **0x**(Enter you USB product ID code)

Save epkowa.conf and proceed to step 3.

For example my epkowa.conf look like this:

#usb 0x04b8 0x0110
usb 0x04b8 0x083c

3) Still in /etc/sane.d edit dll.conf (gedit /etc/sane.d/dll.conf)

Look for the lines that say:

epjitsu
epson
epson2
fujitsu

Comment out both epson entries and add epkowa to this list:

epjitsu
[B]epkowa
#[/B]epson
**#**epson2
fujitsu

Save dll.conf and exit your editor and terminal.

4) Go to System > Administration > Users and Groups 

Unlock with password and click Manage Groups - then open group called **saned** and make sure that any scanner users are members of the group

Exit and reboot and your scanner should be up and running in xsane!

---

