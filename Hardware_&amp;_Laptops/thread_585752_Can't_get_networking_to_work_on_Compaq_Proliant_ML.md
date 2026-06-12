---
title: "Can't get networking to work on Compaq Proliant ML350 server"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by socceroos on 2007-10-21
Hello everyone,

I'm trying to install Ubuntu Server 7.10 on my Compaq ML350 G2 server.

When installing I get the error, "No network devices were detected" blah blah blah. The networking card seems a little odd as it also has the connection to the monitor on it.

Its funny though, because FreeBSD 6.1 installs fine and finds the network card. But Gutsy wont.

I've tried downloading the drivers for the card from HP's site - they didn't have anything for Ubuntu, but they did have an RPM that I converted to a DEB with alien. But that hasn't seemed to work either. I've also tried manually adding in some networking details into /etc/network/interfaces but that doesn't work either!

I'm stuck! I know that Fedora, Suse and FreeBSD all support the card, but I want to use Ubuntu.

Any help would be greatly appreciated!

Socceroos

---

### Post by socceroos on 2007-10-21
Here is a link to the driver download from HP's site:

[http://h18023.www1.hp.com/support/fi...oad/25277.html](http://h18023.www1.hp.com/support/fi...oad/25277.html)

I converted this rpm to a deb and installed it. Could this be the 'e100' in the lsmod list?

---

### Post by socceroos on 2007-10-22
With this intel driver from HP's site, it gives me an error on startup saying "EEPROM Corrupted".

I tried downloading the source for the e100 driver from sf.net and compile it from there, but it has compile errors (function INIT_WORK on line 2676 of e100.c is getting three parameters when it only takes two). I'm not proficient enough with C to be able to fix this coding issue!

Does anyone else have any ideas on this? Could this be a kernel thing with 2.6.22-server?

The network interface is detected as an Intel Pro 100 on boot, but running lshw tells me that it is "UNCLAIMED".

Any help would be much appreciated!

---

### Post by socceroos on 2007-10-22
Fixed.

I did a fresh install with the Ubuntu Server 7.10 cd and after it had told me that it could not detect the network interface I pressed ALT-F2 to bring up a command line and then typed in these commands:

# modprobe e100
# modprobe eepro100

Then I pressed ALT-F1 to get back to the installer and I selected 'Go Back' and then reselected 'Detect Network Devices' from the list and it worked.

---

