---
title: "acpi conflicts with nvidia and wifi!"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by rykel on 2005-12-18
hi,

hope you can perhaps help me with these 2 problems concerning acpi... if acpi is ON, then the following occurs:

[INDENT]1. my official nvidia driver will NOT load the GUI. i have to revert to the "nv" driver. using acpi=noirq or pci=noacpi watever does NOT help.

2. my wifi will NOT detect the wireless networks around me. not even if i turn on and off the wifi button. if i recall correctly, even the wifi card itself cannot be detected. it is a simple intel PRO b/g.[/INDENT]

thanks for your answers!!

---

### Post by 23meg on 2005-12-18
What Nvidia chip do you have? Can you post your /var/log/Xorg.0.log file after reproducing the failure?

Please put in clear terms whether your network device is detected in Device Manager and Networking under the System menu.

---

