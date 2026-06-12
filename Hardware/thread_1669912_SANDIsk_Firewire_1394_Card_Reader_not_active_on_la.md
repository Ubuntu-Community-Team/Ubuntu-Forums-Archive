---
title: "SANDIsk Firewire 1394 Card Reader not active on laptop"
date: 2011-01-18
forum: Hardware
---

### Post by DantePasquale on 2011-01-18
Hi,

I got a new SanDisk CF Card Reader that has a 1394B connection. I got a cable that connects 1394 (regular 4pin) to the 1934B on the SanDisk. The laptop has the regular 1394 connection. However, when I cable it together and pop in a CF card, nothing happens. Nothing noted in /var/log/syslog or dmesg.

It looks like the proper drivers are loaded, so I'm really confused. Could it be that the 1934B won't work with regular 1394? I need to figure this out so I can return it for USB version if it's not compatible.

Is it because there's no power using the 4-pin? (as you can tell, I know nothing about firewire!):

```
What it lacks (and why not perfect) is external power or powered adapter to work with the common iLink 1394 4-pin connectors, which do not have power (just data connection).

```

```

lspci -v 

0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
        Subsystem: COMPAL Electronics Inc Device 0026
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f8300000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ohci1394
        Kernel modules: firewire-ohci, ohci1394
```

```
dante@dexter:~/Documents/Projects/Verizon/SNMP$ lsmod | grep 1394
snd_pcm_oss            41394  0 
ohci1394               30260  0 
ieee1394               94771  2 sbp2,ohci1394
```

```
dante@dexter:~/Documents/Projects/Verizon/SNMP$ modinfo ohci1394
filename:       /lib/modules/2.6.32-27-generic/kernel/drivers/ieee1394/ohci1394.ko
license:        GPL
description:    Driver for PCI OHCI IEEE-1394 controllers
author:         Sebastien Rougeaux <sebastien.rougeaux@anu.edu.au>
srcversion:     53E4506D9E764E5FFCD056C
alias:          pci:v*d*sv*sd*bc0Csc00i10*
depends:        ieee1394
vermagic:       2.6.32-27-generic SMP mod_unload modversions 
parm:           phys_dma:Enable physical DMA (default = 1). (int)
dante@dexter:~/Documents/Projects/Verizon/SNMP$ modinfo ieee1394
filename:       /lib/modules/2.6.32-27-generic/kernel/drivers/ieee1394/ieee1394.ko
license:        GPL
srcversion:     358FFCB6613AF4EEFA19E23
depends:        
vermagic:       2.6.32-27-generic SMP mod_unload modversions 
parm:           ignore_drivers:Disable automatic probing for drivers. (int)
parm:           fcp:Map FCP registers (default = 1, disable = 0). (int)
parm:           disable_nodemgr:Disable nodemgr functionality. (int)
parm:           disable_irm:Disable Isochronous Resource Manager functionality. (bool)

```

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

uname -a
Linux dexter 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

```

---

