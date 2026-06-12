---
title: "Marvell 9182 RAID 0"
date: 2013-02-16
forum: Hardware
---

### Post by Ioncloud on 2013-02-16
I have an Asus Maximus IV Extreme-Z motherboard, and my particular issue is the Marvell 9182 controller (RAID Mode)

I tried Googling around and all the commands I found basically led me to believe that the controller just doesn't exist to Ubuntu. Are there some drivers I could be missing?

---

### Post by Yellow Pasque on 2013-02-16
See if it lists a driver (and post the relevant lspci output for that device)
```
sudo update-pciids
sudo lspci -v
```

---

### Post by Yellow Pasque on 2013-02-16
From looking at latest kernel code, it looks like 9172 is supported, but not 9182: [https://github.com/torvalds/linux/blob/master/drivers/ata/ahci.c#L389](https://github.com/torvalds/linux/blob/master/drivers/ata/ahci.c#L389)

---

### Post by Ioncloud on 2013-02-17
heh, 1 digit separates me from success :)

Here's the output if it helps

0b:00.0 RAID bus controller: Marvell Technology Group Ltd. Device 91a2 (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device 8493
	Flags: bus master, fast devsel, latency 0, IRQ 11
	I/O ports at c040 [size=8]
	I/O ports at c030 [size=4]
	I/O ports at c020 [size=8]
	I/O ports at c010 [size=4]
	I/O ports at c000 [size=16]
	Memory at f6310000 (32-bit, non-prefetchable) [size=512]
	Expansion ROM at f6300000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting

---

### Post by Yellow Pasque on 2013-02-17
Maybe this trick will help?
[http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE91xx_chipsets_Linux_support](http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE91xx_chipsets_Linux_support)

---

### Post by Ioncloud on 2013-02-17
that seemed to work it brought up the drive and I was able to browse around it. Rebooted and it went away. is there a more permanent place to add that to?

---

### Post by Ioncloud on 2013-02-17
I added 
/bin/echo 1b4b 91a2 > /sys/bus/pci/drivers/ahci/new_id

to my /etc/rc.local and set it +x

seems to work once booted!

Thanks for the help :)

---

