---
title: "Automate creation of UDEV rules with serial/user match?"
date: 2008-07-14
forum: General Help
---

### Post by golubovsky on 2008-07-14
Hi,

Is there any tool packaged with Ubuntu which could help automate writing UDEV rules/permissions for the following scenario:

Several users work on the same desktop computer from time to time, not simultaneously. (one keyboard, one monitor).

1. Each user posesses one or more USB storage devices, each device has a serial number SYSFS(serial).

2. When a USB device is first plugged in, its owner user runs the tool which registers the username/serial pair. If a serial is registered to someone else, the tool rejects registration.

3. Based on this, UDEV rules are created, based on serial, so that once the device is plugged in, it is mounted automatically, with permissions assigned so that only the user matching the serial can access it.

I could probably write something like this myself, just curious if such thing is already available.

Thanks.

---

