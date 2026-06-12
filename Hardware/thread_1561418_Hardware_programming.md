---
title: "Hardware programming"
date: 2010-08-26
forum: Hardware
---

### Post by Zacinfinite on 2010-08-26
Can anyone please tell me where to find hardware programming resources with examples.
Need to learn device driver programming along with designing custom circuits.
eg. Stepper motor, LED display segment etc.




PS: URL and torrents are welcomed

---

### Post by leg on 2010-08-26
Somewhere to start:

[Linux Device Drivers book]("http://lwn.net/Kernel/LDD3/")

& look at some of the articles here:

[Linux Devices]("http://www.linuxfordevices.com/")

Good Luck

---

### Post by Lars Noodén on 2010-08-26
Stepper motors can be be controlled using existing GPIO drivers via shell, perl, or python scripts.  Fedora and Debian have GPIO support which may match your hardware, the debian modules should be easiest to port over to Ubuntu.  

Drivers and modules are the same thing and you'll need to be efficient with C.  There is lots of material on [kernel hacking](http://www.ibm.com/developerworks/linux/tutorials/l-kernelhack2/section4.html).

---

