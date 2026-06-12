---
title: "Problem solved - no CDROM at Feisty install (ata_piix)"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by Yuri77 on 2007-07-25
First, the problem description:
While trying to install Ubuntu Feisty Fawn on MSI EX600 laptop, the cdrom disappeared at some stage during the loading of the live cd. The live cd of Edgy loaded fine. It was possible to install Edgy and then upgrade to Feisty, but with Feisty cdrom was missing :( However, when  the kernel 2.6.17.10 from edgy was loaded, cd was fine. 

The problem appeared to be with incorrect handling of the SATA controller with newer ata_piix driver. In this laptop there is a SATA hard drive and IDE DVD drive.

Relevant results of sudo lspci -vv command:

```

00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3fe9
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-

        Latency: 0
        Interrupt: pin B routed to IRQ 21
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at ffa0 [size=16]
        Region 5: I/O ports at ff90 [size=16]
        Capabilities: [70] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

Relevant results of sudo lspci -vvn command (note the identifier 8086:2828, it is important.) :

```

00:1f.2 0101: 8086:2828 (rev 03) (prog-if 80 [Master])
        Subsystem: 1462:3fe9
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 21
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at ffa0 [size=16]
        Region 5: I/O ports at ff90 [size=16]
        Capabilities: [70] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

After some googling and trying of different workarounds (like loading piix instead of ata_piix driver) with no avail, I an my colleague compared the source code of ata_piix driver from edgy (kernel 2.6.17.10) and from feisty (kernel 2.6.20.16). 
The lines 235,236 of newer ata_piix.c (this line in according to the identifier 0x2828 handles the problematic device):

	/* Mobile SATA Controller IDE (ICH8M) */
	{ 0x8086, 0x2828, PCI_ANY_ID, PCI_ANY_ID, 0, 0, ich8_sata_ahci  },

In the older (working) ata_piix.c the line that handles this was as follows:

        { 0x8086, 0x2828, PCI_ANY_ID, PCI_ANY_ID, 0, 0, ich6_sata_ahci  },

Note that the only difference is 6 instead of 8 in  ichX_sata_ahci definition.

So we changed this line to be like in the older ata_piix, re-compiled this driver and... all works! :)
If you want to try this approach, note that the device identifier can be different in your computer, so check the line in the ata_piix.c that matches your device.
The compilation is fairly easy. You need  kernel sources (to get ata_piix.c file), linux headers for the kernel and build-essential. 
Copy  ata_piix.c somewhere and prepare a makefile:

```

obj-m := ata_piix.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules 

```

Than change the .c file and type
 ```

make
 
```

The file ata_piix.ko should be moved to the drivers directory:

```

sudo mv ata_piix.ko  /lib/modules/2.6.20-16-generic/kernel/drivers/ata/

```

Then you need to rebuild initramfs:
```

sudo update-initramfs -u

```

Restart the computer.

Looks like the ata_piix driver needs a patch. I would file a bug report, but I'm not sure were does it belong, so any advice would be appreciated.

Hope it will help someone, this problem looks quite common, and not only in Ubuntu, because with Suse 10.2 and Debian 4 it was a same problem.

---

