---
title: "Lenovo Yoga 900 and undetected ACPI PNP devices"
date: 2016-03-23
forum: Hardware
---

### Post by kfhughes on 2016-03-23
I'm running 15.10 on a Yoga 900 convertible with the 4.5 stock kernel, and most things work in one way or another except detecting whether it's in laptop or tablet mode.  I've looked through the kernel logs and check the devices detected by the ACPI subsystem, and found that PNP0C60 isn't detected.  Actually, none of the PNP0Cxx values above xx=14 are detected.

I've had no success reassembling the DSDT yet, so I'm hoping someone has another idea what I can try?  Is there a way to manipulate object in the ACPI namespace to at least query the state?

---

