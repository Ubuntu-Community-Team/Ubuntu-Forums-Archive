---
title: "Intel Atom x5-E8000/J3xxx/N3xxx &quot;Imaging Unit&quot; webcam"
date: 2024-05-22
forum: Hardware
---

### Post by hbandi on 2024-05-22
Hi,
i have a Lenovo convertible tablet / detachable laptop with front and rear cameras.
probably this the webcam device (lspci) :

00:03.0 Multimedia controller [0480]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit [8086:22b8] (rev 36)

people says likely the kernel modules ov2680 and ov5670 are which drive these devices.
i loaded them, but no new v4l2, no /dev/video* device appeared in the system.
these drivers are relatively new in the kernel tree, so i guess they are not fully completed yet.

on linux-hardware.org, only 1 probe said this PCI device green: [URL="https://linux-hardware.org/?probe=aaa295fa26"]https://linux-hardware.org/?probe=aaa295fa26
[/URL]but no dmesg message about a webcam even there.

whom do I need to bribe to write a working driver for these webcams?
did i buy a wrong tablet?

---

