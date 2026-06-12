---
title: "via VT6421 PCI SATA Card"
date: 2009-11-07
forum: Hardware
---

### Post by conradin on 2009-11-07
Hi all, 
I have a PCI Sata Card I am trying to use. Im not sure whats going on with it. i do not see my hard drive listed any place.

I used the command lspci -vvv
and somewhere down in the data it dumped to the screen was what looks like my PCI card. Can any one tell me where to go from here? How do I get my hard drives to work? ( i just want the data, Im not concerned with setting up RAID)

01:01.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at d080 [size=16]
	Region 1: I/O ports at d000 [size=16]
	Region 2: I/O ports at df00 [size=16]
	Region 3: I/O ports at de80 [size=16]
	Region 4: I/O ports at de00 [size=32]
	Region 5: I/O ports at dd00 [size=256]
	Expansion ROM at ee200000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

---

### Post by conradin on 2009-11-10
Solved:: Installed Windows. Got data no problems.

---

### Post by valentt on 2009-11-29
I found the answer on how to make this VIA VT6421 card work on Ubuntu:

sudo modprobe sata_via

more details on my blog:
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)

---

### Post by cadcam on 2010-12-06
ok, I'm running maverick.  

i have had no problems seeing the drives on the card.

my problem is.... I am RAID 1 on two disks.  the disks still come into ubuntu as sdc and sdc.  they should be listed as one disk.  i've attempted to use the stuff from the manufacter, but I can't compile anything becuase its too old??????

help?

thks,
A

---

