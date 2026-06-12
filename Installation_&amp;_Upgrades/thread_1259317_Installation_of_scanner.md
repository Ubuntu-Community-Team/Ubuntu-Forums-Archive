---
title: "Installation of scanner"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by santana99 on 2009-09-06
I'm trying to install the DCP7025-scanner from Brother under Kubuntu 9.04. Loaded the packages sane and xsane and managed to get the scanner up and running as root (sudo xsane etc. works fine). Can't get it running as a normal user. Have seen multiple solutions which are based on editing permission-rules in /etc/udev/rules.d - directory. The basic problem that I have is that these files like 40-basic-permission.rules don't exist on my machine. I tried to create one with the following settings:

# This file establishes permissions and ownership of devices according
# to Ubuntu policy. See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console", MODE="0600"
KERNEL=="ptmx", MODE="0666"
KERNEL=="tty", MODE="0666"
LABEL="vc_end"

# Miscellaneous devices
KERNEL=="null", MODE="0666"
KERNEL=="zero", MODE="0666"
KERNEL=="full", MODE="0666"
KERNEL=="random", MODE="0666"
KERNEL=="urandom", MODE="0666"
KERNEL=="inotify", MODE="0666"

But that doesn't solve the problem.

Do I need to install another package which then creates a rule-file?

Thanks for your help.

Jan

---

### Post by santana99 on 2009-09-12
Can anyone please help ....:D:D:D:D

---

