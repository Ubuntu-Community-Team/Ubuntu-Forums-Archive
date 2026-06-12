---
title: "Requesting: [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
date: 2009-03-02
forum: Hardware
---

### Post by Marlon. H. on 2009-03-02
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

```
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: driver=sisfb latency=0 module=sisfb

```

```
marlon@ubuntu:~$ lsmod | grep sis
sisfb                 253012  1 
sis_agp                15232  0 
agpgart                42184  2 sis_agp,amd64_agp
pata_sis               18436  1 
libata                178208  3 pata_acpi,ata_generic,pata_sis

```

Is there any existing driver for that graphics card? I have just installed Ubuntu for the first time.

When I try to enable desktop effects the following is displayed:

> Desktop effects could not be enabled

From what I read on the net, it seems to because there is no Linux driver for the card.

If somebody has the link to it,kindly post it. Thanks.```

```

---

### Post by cariboo on 2009-03-03
You  can try [here]("http://www.sis.com/download/"), but it doesn't look like there are drivers for your chipset.

Jim

---

### Post by higgins on 2009-08-04
> **Marlon. H. said:**
> ```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

```
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: driver=sisfb latency=0 module=sisfb

```

```
marlon@ubuntu:~$ lsmod | grep sis
sisfb                 253012  1 
sis_agp                15232  0 
agpgart                42184  2 sis_agp,amd64_agp
pata_sis               18436  1 
libata                178208  3 pata_acpi,ata_generic,pata_sis

```

Is there any existing driver for that graphics card? I have just installed Ubuntu for the first time.

When I try to enable desktop effects the following is displayed:



From what I read on the net, it seems to because there is no Linux driver for the card.

If somebody has the link to it,kindly post it. Thanks.```

```

Does this page help: [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)

---

