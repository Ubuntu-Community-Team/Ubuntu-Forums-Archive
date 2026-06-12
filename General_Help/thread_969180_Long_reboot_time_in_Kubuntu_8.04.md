---
title: "Long reboot time in Kubuntu 8.04"
date: 2008-11-03
forum: General Help
---

### Post by DarkBeer on 2008-11-03
Running Kubuntu 8.04 on a Dell PowerEdge 840.  When I reboot the server after a kernel update, it takes close to 10 minutes for the restart to complete.  Looking through dmesg I found the following:

[   48.567498] kjournald starting.  Commit interval 5 seconds
[   48.567512] EXT3-fs: mounted filesystem with ordered data mode.
[   55.919416] NET: Registered protocol family 10
[   55.919632] lo: Disabled Privacy Extensions
[  447.360370] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  447.384480] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  447.402647] EDAC MC: Ver: 2.1.0 Aug 20 2008
[  447.459365] EDAC MC0: Giving out device to 'i3000_edac' 'i3000': DEV 0000:00:00.0
[  447.459426] EDAC PCI0: Giving out device to module 'i3000_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)

There is a pause of almost 400 seconds before the pci_hotplug entry.  Is that what is causing the delay, or can someone shed any light on what might be causing this problem?
Thanks!

---

### Post by prshah on 2008-11-03
> **DarkBeer said:**
>   Is that what is causing the delay, or can someone shed any light on what might be causing this problem?


I'd suggest you [install bootchart]("apt://bootchart"): (or, Manually): Open a terminal (Applications-Accessories-Terminal) and give the command
```

sudo apt-get install bootchart
```

Now, on every boot a graphical progress chart is created in "/var/log/bootchart". Post the bootchart files for a clue as to what could be wrong.

---

### Post by DarkBeer on 2008-11-04
Bootchart attached:

---

