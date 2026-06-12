---
title: "Finding Device/NIC Make/Model (for WOL)"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by moon2js on 2007-02-05
Generally, how does one find out the make and model of a device from a terminal? In GUI/desktop environments, there is usually some device manifest or manager that shows you a list of devices and drivers. I'd like to know the make and model of my ethernet NIC.

Specifically, I'm trying to troubleshoot WOL functionality. I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=234588&highlight=wol") but no luck (despite the BIOS being configured), so my next steps are to look into the NIC and see if it has any history.

Also, next time I have access to the machine, I'd like to see if the ethernet light is on when the machine is off. But in the meantime, I'd like to research the device.

Any suggestions?

---

### Post by lloyd_b on 2007-02-05
Two terminal commands for you:

"lspci" - lists all PCI devices on a computer
"lshw" - lists all attached hardware on the computer

There's obviously going to be overlap between the two.  Just run both, and search through the results for "Ethernet".   This may not tell you the actual brand name of the NIC, but it should provide enough details to identify the specific chipset that it uses (and consequently, which driver it should use and what it's capabilities are).

Lloyd B.

---

### Post by moon2js on 2007-02-05
Those were precisely the commands I was looking for. Thanks you!

---

