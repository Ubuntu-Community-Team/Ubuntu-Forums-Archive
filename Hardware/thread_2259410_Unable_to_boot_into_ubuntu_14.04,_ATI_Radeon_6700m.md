---
title: "Unable to boot into ubuntu 14.04, ATI Radeon 6700m"
date: 2015-01-04
forum: Hardware
---

### Post by hkundnani on 2015-01-04
The image attached shows the error which i am recieveing. I tried each and every possible way through recovery mode but still not able to boot into ubuntu. I know this problem is related to graphics driver because when i tried to boot in fails safe graphics mode i was able to but normally i just can't boot into ubuntu. If i wait for some time after these error messages are shown the laptop fan starts to run in full speed as if the graphics card is getting heated up. Graphics card i am using is ati radeon 6700m series
Please any help will be appreciated.

---

### Post by nickajeglin2 on 2015-01-04
I think that radeon cards are not as well supported as nvidia, but someone please correct me if that's not right anymore.

In any case, you could try adding some boot parameters like "nomodeset" or "acpi=off"

if nomodeset works, you can later permanently add it to your boot parameters, but I think that running with "acpi=off" is a pretty bad idea, especially on a laptop.

look here: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) for an explanation of how to use the boot options.

If you get it up and running with either of those, you could try installing different graphics drivers until you hit one that works well.

---

