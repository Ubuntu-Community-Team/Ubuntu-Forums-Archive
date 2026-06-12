---
title: "Udev permanent device symlinks in Hardy?"
date: 2008-05-09
forum: Hardware
---

### Post by aizhiguo on 2008-05-09
I am having issues with my mouse and tablet getting new **/dev/input/event*** handlers every time I reboot (in Hardy). This pooches my delicately-crafted xorg.conf, which works great when each "InputDevice" section is pointed at the right "Device".

I'm trying to create permanent device symlinks in /dev/ by adding the following code to **/etc/udev/rules.d/010_local.rules** :

```

BUS=="usb", KERNEL=="event*", SYSFS{product}=="UC-LOGIC Tablet WP8060U", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
BUS=="usb", KERNEL=="event*", SYSFS{product}=="Logitech USB-PS/2 Optical Mouse", NAME="input/%k", SYMLINK+="mouse-event", MODE="0666"
```

It isn't working. I don't actually know what I'm doing with udev; these are modeled after the symlink code in:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

What am I doing wrong? Thanks.

**[SIZE="3"]UPDATE:[/SIZE]**

Solved with following code in /etc/udev/:

```
KERNEL=="event*", SYSFS{product}=="Tablet WP8060U", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"
KERNEL=="event*", SYSFS{product}=="USB-PS/2 Optical Mouse", NAME="input/%k", SYMLINK+="mouse-event", MODE="0666"
```

A similar configuration should be useful whenever you've got multiple pointing peripherals with specialized drivers sending core events to a virtual Configured Mouse in xorg.conf.

---

