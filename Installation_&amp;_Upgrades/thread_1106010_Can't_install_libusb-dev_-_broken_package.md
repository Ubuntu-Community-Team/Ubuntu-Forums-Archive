---
title: "Can't install libusb-dev - broken package"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by daxdog on 2009-03-25
I am struggling to install the libusb-dev package.  When I attempt, I get:

```
$ sudo apt-get install libusb-dev
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
  libusb-dev: Depends: libusb-0.1-4 (= 2:0.1.12-8) but 2:0.1.12-12 is to be installed
E: Broken packages
```

When I try to uninstall libusb-0.1-4 I get information that Linux wants to uninstall a whole bunch of other packages.

I have tried "sudo apt-get install -f" and "sudo dpkg --configure -a" but neither had an effect on my problem.

---

### Post by daxdog on 2009-03-26
I upgraded both libusb-0.1-4 and libusb-dev to version 13.

---

