---
title: "Laptop Fan Not Turning Off"
date: 2012-11-13
forum: Hardware
---

### Post by gmseed on 2012-11-13
Installed Ubuntu 12.04LTS on a Toshiba Satellite laptop and for the first 1/2hour aftering booting up the laptop fan can't be heard and functions as expected.

After ~1/2hour the fan comes on and DOES NOT go off again until the m/c is turned off.

I've checked the settings if additional drivers are required and none are listed.

That's me now installed Ubuntu 12/04/12.10 on a Sony Vaio, Samsung Chronos and Toshiba Satellite and had a whole range of problems on all 3 laptops.

I'm absoluetly convinced that Ubuntu desktop can/should only be run on a Dell laptop that has been certified by Ubuntu; the problem being the m/cs are typically a bit out of date and difficult to pruchase. An attempt to install on any other m/c leads to a range of low-level problems, fishing around and firing up the terminal window with varying degrees of success.

Graham

---

### Post by dannyboy79 on 2012-11-13
edit your grub default boot line in /etc/default/grub
from
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="Linux""
```

after you save that file, make sure you run
```
sudo update-grub
```
see if that makes a difference. oh, you'll have to restart the machine I think.

---

