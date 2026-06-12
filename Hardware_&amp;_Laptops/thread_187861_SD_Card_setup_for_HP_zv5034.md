---
title: "SD Card setup for HP zv5034"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by Jeff59 on 2006-06-03
I'm new to Ubuntu and Linux but love it. I have read several post some say it is possible to use the built in sd card reader and some say it is unsupported.  Can some one tell me the facts and guide a newbie?  Thanks:confused:

---

### Post by rado_london on 2006-06-03
HI. I have dv4145ea and 6in1 Texas Instruments card reader. The SD works out of the box with dapper. I dont know why you end up with problem. Are you running Dapper?

---

### Post by Jeff59 on 2006-06-04
Yes just installed Dapper.  Do you have to mount the card reader?

---

### Post by nolongerlivecd on 2006-06-04
Sorry to hijack, but I have an Acer Aspire 5500 and i'm facing problems with my SD card reader as well. 

lspci reveals:

0000:06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
0000:06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
0000:06:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
0000:06:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520 (rev 01)
0000:06:04.4 FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)

---

### Post by rado_london on 2006-06-04
[QUOTE=Jeff59]Yes just installed Dapper.  Do you have to mount the card reader?[/QUOTE]
Once you insert the card it should automount it. At least me this is the case.

---

### Post by HankB on 2006-06-04
I have an HP L2000 and the built in card reader works on it (at least for SD cards). It identifies itself (using lspci -v) as:
```


0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at c0206000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2

0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at c0209400 (32-bit, non-prefetchable) [size=256]
        Memory at c0209000 (32-bit, non-prefetchable) [size=256]
        Memory at c0208400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

(END)

```

It gets mounted automagically and I think that is a function of gnome. I'm not sure if other desktops do that too. When I plug it in, dmesg reports:
```

[ 7758.667868] mmcblk0: mmc2:a95c SD128 123008KiB
[ 7758.667908]  mmcblk0: p1
[ 7758.945261] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by ophion on 2006-06-14
The card reader in my Toshiba laptop is not working either.

lshw says:

*-storage UNCLAIMED
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                resources: iomemory:b8004000-b8005fff irq:10

---

