---
title: "[SOLVED] Notebook MSI M670: no suspend, no hibernate, no webcam"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by espi3d on 2007-12-27
Hi, I installed Ubuntu Desktop 7.10 in my brand new MSI Megabook M670 (Sempron 3600+, nForce MCP51M, GeForce Go 6100), but first I had to boot the Live CD with acpi=off kernel option, otherwise it would hang at usplash. Then, when Ubuntu is installed, I had to append the options "noapic nomce nosmp" as kernel params to the Ubuntu entry in /boot/grub/menu.lst in order to boot the system, again: otherwise it would only display a white screen instead of usplash and then hang. Then, I discover the suspend and hibernate features doesn't work properly: every time I suspend or hibernate de machine then I can't wake it up. The only thing I can do in that state is a hard reset.
On the other hand, the integrated webcam doesnt work with ubuntu. Kopete shows just a blue surface instead of an image of me. The lsusb gives me the device as "0c45:624f Microdia".

What can I do to solve those issues?

Thanks in advance.

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:8105

---

