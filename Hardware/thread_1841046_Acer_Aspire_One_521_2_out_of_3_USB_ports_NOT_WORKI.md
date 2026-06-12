---
title: "Acer Aspire One 521 2 out of 3 USB ports NOT WORKING"
date: 2011-09-08
forum: Hardware
---

### Post by dadopap on 2011-09-08
Hi,

I have installed ubuntu 11.04 on my new acer aspire one 521 the one with amd V105 CPU and ati radeon 4200.

everything works like a charm (I have even patched the kernel to fix the battery icon problem) but 2 out of 3 USB ports do not work.

under win7 starter they perfectly work but not under linux.

The port working is the one on the left side. two ports on the right side do not work. I have tried them with a usb pen drive.

I know that Linux has some problems with USB I had it on my old laptop with ubuntu 8.04.

I've looked on the internet for the problem but I haven't found anything.

If I run lsusb with the pen drive attached to the working port it shows it correctly while for the "dead" ports it does not show anything.

any idea for the fix?

---

### Post by dadopap on 2011-09-09
Ok I fixed it,

I rebooted with the old kernel and all USB worked so I recompiled the whole kernel again and now USB works.

A little weird but OK!

---

