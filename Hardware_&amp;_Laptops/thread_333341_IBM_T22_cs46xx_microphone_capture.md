---
title: "IBM T22 cs46xx microphone capture"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by bzimage2 on 2007-01-07
Hi, Just wanted to share this.

Ubuntu v6.10 and IBM Thinkpad T22 with a cs46xx sound chip.

To get the recording capture for microphone to work I had do disable acpi with "acpi=off". I did this in /boot/grub/menu.lst by adding it to the following line:

kernel    /boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro quiet splash acpi=off

I did some test recordings with Audacity that worked fine.

/Regards

---

