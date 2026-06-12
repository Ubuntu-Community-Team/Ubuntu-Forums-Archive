---
title: "Broken Package on Dell Inspiron 8600 with ATi 9600"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by gkwong on 2007-10-20
I have a Dell 8600 with an ATi Radeon 9600 and I'm trying to enable the restricted drivers for it on Ubuntu 7.10. But when I click "enable" I get the message "Could not apply changes! Fix broken packages first." I went into system/softwaresources and enabled "community-maintained open source software" and "proprietary drivers for devices." I also went into the terminal and tried "sudo apt-get install fglrx-control" but this is what I get:

> gary@gary:~$ sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  fglrx-control: Depends: xorg-driver-fglrx but it is not going to be installed
                 Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but it is not installable
E: Broken packages


What do I do now?

---

