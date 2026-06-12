---
title: "Ubuntu Arm Beaglebone Black Failure Concerns"
date: 2013-07-31
forum: Hardware
---

### Post by teaker1s on 2013-07-31
I purchased a beaglebone black and installed ubuntu CLI to sd card leaving the angstrom linux on eMMC.

I pulled Lubuntu-desktop to sd card and all appeared fine until I issued reboot command.

I then found trying to boot angstrom that HDMI no longer operated and ssh password on angstrom was neither default on ubuntu or angestrom.

angstrom web interface was still operational but ssh refused to log on complaining password was wrong

I was advised to reinstall angstrom to eMMC and as it booted off sd card the HDMI worked, it appeared to flash correctly until reboot.

The beaglebone hardware developer has supported me in trying to resurrect the device and we have been unsuccessful.

Now either a remarkable hardware failure or some how the installation of ubuntu and lubuntu desktop corrupts device bootloader in a manner that isn't reversible with eMMC reflash.

I would like to report this as a bug/issue but am not sure how to correctly report it.

A replacement device should be issued to me in due course, but I am less than keen to try again without knowing exactly what happened.

thanks

---

