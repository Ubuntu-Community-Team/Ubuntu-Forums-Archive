---
title: "brother printer driver"
date: 2011-05-22
forum: Hardware
---

### Post by tetsu7 on 2011-05-22
i bought a brother mfc-9970cdw laser printer thinking it would work on my amd64 ubuntu v.10.10 as i saw linux drivers on brothers website [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
as it turns out they have rpm and deb drivers however they are all i386 and i need amd64. is there any way to convert these drivers from i386 to amd64 or some other way to get this printer to work? or should i just take the printer back and buy something from a different manufacturer?

---

### Post by wojox on 2011-05-22
No but you can install the 32 bit libs and it will work.

```
sudo apt-get update; sudo apt-get install ia32-libs
```

and make sure you run **sudo dpkg -i --force-architecture** on the packages.

---

### Post by tetsu7 on 2011-05-22
thanks alot that installed the cupswrapper driver! the lpr driver failed, i think: sudo dpkg -i --force-architecture mfc9970cdwlpr-1.1.1-5.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 564528 files and directories currently installed.)
Preparing to replace mfc9970cdwlpr 1.1.1-5 (using mfc9970cdwlpr-1.1.1-5.i386.deb) ...
Unpacking replacement mfc9970cdwlpr ...
Setting up mfc9970cdwlpr (1.1.1-5) ...
mkdir: cannot create directory `/var/spool/lpd/mfc9970cdw': No such file or directory
chown: cannot access `/var/spool/lpd/mfc9970cdw': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc9970cdw': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc9970cdw': No such file or directory

im not even sure what an lpr driver is, does this even matter since it prints now with the cupswrapper driver? a little off topic, im trying to get the scanner and fax to work however when i open xsane it opens for my old hp psc1310. how can i get it to show my brother mfc-9970cdw? my brother is plugged into a switch via rj45 thats hooked up to my router. my hp psc 1310 is plugged into my computer via usb. and thanks again for your help! you are awesome!

---

### Post by wojox on 2011-05-23
To install the lpd run:

```
sudo makedir /var/spool/lpd
```

Then try to install it like you did.

To fix the scanner:

```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
```

Add the following Before the line "#":

```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```

Restart the OS.

---

### Post by tetsu7 on 2011-05-23
the printer is good thanks to you! however i still cant get to my brother scanner it is stuck on hppsc1310 i go to simple scan/preferences/scan source all i see is the hp. i added the line you indicated and restarted my system and still the same. my printer is hooked up to a switch thats on my router so i also plugged it straight to my system via usb still the same. below is where i added the line you told me to add.
# This file was automatically created based on description files (*.desc)
# by sane-desc 3.5 from sane-backends 1.0.21 on Thu Jul  8 02:56:44 2010
#
# udev rules file for supported USB devices
#
# To add a USB device, add a rule to the list below.
#
# To run a script when your device is plugged in, add RUN+="/path/to/script"
# to the appropriate rule.
#
# If your scanner isn't listed below, you can add it as explained above.
#
# If your scanner is supported by some external backend (brother, epkowa,
# hpaio, etc) please ask the author of the backend to provide proper
# device detection support for your OS
#
# If the scanner is supported by sane-backends, please mail the entry to
# the sane-devel mailing list (sane-devel@lists.alioth.debian.org).
#
ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}!="usb_device", GOTO="libsane_rules_end"

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

---

### Post by Dave Smith on 2011-10-16
I found this information which might help you:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

