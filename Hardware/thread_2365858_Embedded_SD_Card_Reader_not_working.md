---
title: "Embedded SD Card Reader not working"
date: 2017-07-11
forum: Hardware
---

### Post by vezinadj on 2017-07-11
I have installed Ubuntu 16.04 and cannot seem to get the internal SD card reader working on the PC. I have a 4GB and 64GB card that I have tried to get working with no luck. 

Here is some general information from the lspci output:

```

user@u1604dev:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 11)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 11)
00:12.0 SD Host controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SDIO Controller (rev 11)
00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 11)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 11)
00:17.0 SD Host controller: Intel Corporation Atom Processor E3800 Series eMMC 4.5 Controller (rev 11)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 11)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 11)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 11)
00:1c.1 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 (rev 11)
00:1c.2 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 3 (rev 11)
00:1c.3 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 4 (rev 11)
00:1e.0 DMA controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series LPIO1 DMA Controller (rev 11)
00:1e.3 Communication controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series LPIO1 HSUART Controller #1 (rev 11)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 11)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 11)
01:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
02:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
03:00.0 Unassigned class [ff00]: Beckhoff GmbH Device 5000 (rev 02)

```


It looks like the SD Host controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SDIO Controller (rev 11) is the SD card reader built-in.

Here is the kernel version:

```

user@u1604dev:~$ uname -r
4.8.0-58-generic

```


This is the kernel output for anything related to the sdhci driver

```

user@u1604dev:~$ dmesg | grep sdhci
[    2.971258] sdhci: Secure Digital Host Controller Interface driver
[    2.971261] sdhci: Copyright(c) Pierre Ossman
[    3.060667] sdhci-pci 0000:00:12.0: SDHCI controller found [8086:0f16] (rev 11)
[    3.060855] sdhci-pci 0000:00:12.0: BAR 0 is not iomem. Aborting.
[    3.061006] sdhci-pci 0000:00:17.0: SDHCI controller found [8086:0f50] (rev 11)

```

The "BAR 0 is not iomem. Aborting" makes it seem that the sdhci driver is not playing well with the device. Has anyone experienced any issues with the built-in intel card readers?

---

### Post by Futant on 2017-07-11
Does it work if you restart the computer while the card is inserted? Had this problem for a long time, an update fixed it in the end.

---

### Post by efflandt on 2017-07-11
Note that if you do get your internal card reader working, you would need **exfat-utils** package (which should also include exfat-fuse for auto mounting) if the 64 GB SD(XC) is using exFAT file system which is default for larger than 32 GB SD. So see if you can get the 4 GB SD recognized first, which by default would be FAT32 unless you changed it.

But I am not familiar with Atom CPU or why it lists (2) SD Host Controllers. My slowest PC is a tablet PC with 1 GHz 2-core AMD C-50 and its SD slot is internally USB connected. So it is able to boot Ubuntu from SD slot (most mmc slots cannot boot).

---

### Post by vezinadj on 2017-07-12
This PC I am using is an industrial rated PC that uses a CFast card as its main storage device which is probably why there is two host controllers. I have tried keeping the card in the PC and rebooting and was still unable to see the 4GB. 

I didn't know if there was a specific driver I was missing with the built-in internal SD card readers for the Atom.

---

