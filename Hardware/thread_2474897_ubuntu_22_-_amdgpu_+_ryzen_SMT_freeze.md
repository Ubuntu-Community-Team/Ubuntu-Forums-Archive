---
title: "ubuntu 22 - amdgpu + ryzen SMT freeze"
date: 2022-05-11
forum: Hardware
---

### Post by lhommev on 2022-05-11
Hi,

I'd like to report this issue after spending a month to narrow this down to the culprits. I found a workaround fortunately. More people can have this issue and thrown their computer by the window because it s very frustrating.  

Issue symptoms:
**Unrecoverable system freeze.** No trace of error in the system logs / dmesg / syslog / kernel.log

My configuration:
Motherboard: msi meg ace x570
CPU: ryzen 5950x
GPU: xfx rx6900
RAM: 4 sticks 32 GB
Disks: 3 x nvme attached on the board
PSU: corsair 850W

Reproduction:
 - It happens sometimes when using GUI applications such as firefox, rawtherapee or darktable (photo edition). 
 - The most likely to trigger is to open rawtherapee, load a photo library, close it and run again -> 80% chance of freeze
 - opening a tab on firefox has a chance to trigger, depending on the content. Seems like ebay has higher risks.
 - scrolling on a web page (rare)
 - doesn't happen when using 3D applications
 - suspend the system and wakeup : freeze at first click (50% chance)

What i tried so far to mitigate the issue with **no result**:
- swapping GPU / pci slot
- swapping CPU ( with another amd card)
- swapping disks
- swapping RAM
- lowering frequencies CPU+RAM to the bare minimum
- increasing voltages significantly
- forcing PCI to gen 2
- disabling C states / SVM / no execute / iommu / core boost  ... everything in bios
- disabling kernel modules: acpi-cpufreq, amd-cpufreq, pcie aspm (pcie power management)
- using kernel 5.15, 5.17, 5.18

What i tied so far that actually have effects:
 - **SMT disabled** in bios -> **freezes never happens**
 - SMT enabled in bios - freezes happens
 - use another operating system

My personal interpretation:
this is not related to a hardware defect. It seems related to transferring data from ram to gpu. Thus rawtherapee freezes the second time because the photos are in cache memory. With simultaneous multithreading, the cpu may send too many data at a time ?

Also windows 10/ ubuntu 20.4 does not have the issue. So i guess the "bug" appeared in kernel 5.15

---

### Post by TheFu on 2022-05-11
Nobody here works for Canonical. You've done some research which would be helpful to the right people.  That ain't us.

Perhaps entering a bug in the bug db would be more helpful?  
[LIST]
[*][https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[*][https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en](https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en) - for supported desktop releases
[*][https://ubuntu.com/server/docs/reporting-bugs](https://ubuntu.com/server/docs/reporting-bugs) - for supported server releases
[/LIST]

Welcome to the bleeding edge.

---

