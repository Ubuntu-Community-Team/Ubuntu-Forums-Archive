---
title: "Disable Specific USB Port in O/S ?"
date: 2020-10-09
forum: Hardware
---

### Post by linuxology on 2020-10-09
Noticed the Kworker process was going very high due to a usb port being in an over current condition by running dmesg at boot. By disabling all of the USB in the BIOS seems to fix the issue.  Is there a way to disable a specific port within the O/S? For the time being I had to disable all of the usb ports via the BIOS.


The message in dmesg output that raised suspicion was usb usb1-port6 overcurrent condition. This caused the CPU to stay around 80% due to the kworker process.

---

