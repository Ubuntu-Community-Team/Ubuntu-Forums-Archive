---
title: "PRO/Wireless 3945ABG"
date: 2008-09-11
forum: Hardware
---

### Post by karamazov777 on 2008-09-11
I have problem with wirless driver
karamazov777@karamazov777-laptop:~$ sudo lshw -C network[sudo] password for karamazov777: 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
How i resolve this?

---

### Post by DoctorMO on 2008-09-11
Odd, your computer should be using the iwl3945 (or iwp3945 for older versions of ubuntu) module.

Try 'sudo modprobe iwl3945'

If that doesn't work let me know. And also double check the computer doesn't have a physical wifi switch that had caused the hardware to be unavailable.

---

