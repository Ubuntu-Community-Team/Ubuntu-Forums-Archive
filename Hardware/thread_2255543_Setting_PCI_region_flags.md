---
title: "Setting PCI region flags"
date: 2014-12-05
forum: Hardware
---

### Post by joeyc1953 on 2014-12-05
So I have a PCI device (a nic) which I'm having trouble getting working.  I see it in lspci/lshw etc. so that's all good, but I'm having trouble using it because I can't get the driver working.  Specifically, when the driver gets probed in, it does some checks and errors out. Diving into the driver code, it looks like the problem is that it expects the IORESOURCE_MEM flags to be set on its index 2 , resource.  Basically, the following check is failing:  > pci_resource_flags(p, 2) & IORESOURCE_MEM  Any thoughts on how to set the flag for this region or to further diagnose the issue?

---

### Post by joeyc1953 on 2014-12-08
As a small update, it looks like resouce2 is not even present under sysfs.

> 
joe@spira:/sys/bus/pci/devices/0000:04:00.0$ ls
broken_parity_status
class
config
consistent_dma_mask_bits
d3cold_allowed
device
dma_mask_bits
enabled
irq
local_cpulist
local_cpus
modalias
msi_bus
numa_node
power
remove
rescan
reset
resource
resource0
rom
sriov_numvfs
sriov_totalvfs
subsystem
subsystem_device
subsystem_vendor
uevent
vendor
vpd
joe@spira:/sys/bus/pci/devices/0000:04:00.0$ 


---

