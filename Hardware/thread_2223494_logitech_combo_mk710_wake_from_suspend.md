---
title: "logitech combo mk710 wake from suspend"
date: 2014-05-11
forum: Hardware
---

### Post by wladyx on 2014-05-11
Hi guys,
I have bought a mk710 logitech combo, and set the following on my ubuntu 14.04 so that the notebook wakes from suspend:

```
cat /etc/udev/rules.d/90-keyboardwakeup.rules:
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52b" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"

grep -i cmdline /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1 acpi_enforce_resources=lax"

```

Waking for suspend works both from keyboard and mouse, but it also wakes only by moving the mouse, which i would like to disable.
So the question would be how to disable the waking by moving the mouse or enable the wakeing only for the keyboard (they are both connected on the same unifying usb dongle) ?
Searched a lot of threads and discussions about this, but hit a brick wall, thanks for any info/suggestions.

---

