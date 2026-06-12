---
title: "SD card reader can't read cards"
date: 2012-02-26
forum: Hardware
---

### Post by bucketoftruth on 2012-02-26
This one is puzzling me.  I have a Dell Latitude e4200.  The SD card reader is detected and the driver is loaded:

```

$ sudo lspci -v
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Device 0277
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f65ff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
```

...

```
$sudo lsmod | grep sdhci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
```

No matter what SD card I insert into the slot, absolutely nothing is detected.  DMESG, syslog, all completely empty of anything when the card is inserted.

Ubuntu 11.04, btw.

Any ideas?

---

### Post by wolfen69 on 2012-02-26
Try this:
```
sudo cp /etc/modules /etc/modules.bak
```
then
```
gksu gedit /etc/modules
```
Tag this on to the end of the file in a new line:
```
tifm_sd
```
reboot

---

