---
title: "Laptop owners: Potential bug causes excessive HD temp"
date: 2009-01-18
forum: Hardware
---

### Post by Tonohono on 2009-01-18
Howdy folks,

This is a heads up/request for feedback concerning bug [#318346]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/318346").

To provide bug assistance:
- Have an Intrepid system patched with **acpi-support_0.114-0intrepid2**.
- Use **hddtemp** or **smartctl** to obtain hard drive temperatures. GNOME users may also want to install **sensors-applet**.
- Switch between AC and battery power and monitor HD temp for several (30+) minutes on each.

- If no change in HD temp is observed, you're in the clear!

- If you experience the same issue as described in the bug report, downgrade to [**acpi-support_0.114**]("http://packages.ubuntu.com/intrepid/acpi-support") and shutdown the system for a few moments to allow HD temp to fall.
- Boot the system and allow the HD temp to rise.
- If on AC power the HD temp maxes out lower than when **acpi-support_0.114-0intrepid2** was installed, please submit the [relevant info]("https://wiki.ubuntu.com/DebuggingACPI#Filing%20a%20Bug%20Report") to the bug report.
- It may also be a good idea to re-upgrade to **acpi-support_0.114-0intrepid2** to see if HD temp increases again.

I hope this bugs affects a small number of laptops (e.g. my HP dv6500), but I feel it should be brought to everyone's attention in case a significant number of laptop hard drives are being subjected to potentially damaging temperatures.

---

