---
title: "How to Run a Script When Connecting a USB GPS"
date: 2008-04-26
forum: Hardware
---

### Post by harbertc on 2008-04-26
I'm trying to automatically run a script when I connect my Garmin GPS (USB). It seems like I should be able to do this by creating an upstart script or a udev rule.

Here is my first attempt, but it doesn't seem to work.

/etc/udev/rules.d/51-garmin.rules:

SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666",RUN+="/bin/echo TESTTESTTEST >> /tmp/garmintest.log"

Any ideas?

---

