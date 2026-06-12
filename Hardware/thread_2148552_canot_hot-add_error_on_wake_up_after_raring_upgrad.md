---
title: "canot hot-add error on wake up after raring upgrade"
date: 2013-05-25
forum: Hardware
---

### Post by twinturbotom on 2013-05-25
I'm looking to clean up some errors that appear after opening a closed macbook air 1,1 lid a dark screen shows up with the following lines:

```
[ 9395.896272] pciehp 0000:00:1c.4:pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
[ 9395.896276] pciehp 0000:00:1c.4:pcie04: Cannot add device at 0000:02:00
```

I then listed pci's for 04 and found:

```

lspci | grep 1c
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
```

lshw:

```
*-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:90400000-904fffff ioport:90600000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
```


My interpretation of all this is that I have an intel on port 1 and port 5, and waking up the machine is attempting to add something adding?  Not sure if there is a script that runs on wake I need to eliminate? or change something else. 

Please let me know your thoughts...

---

