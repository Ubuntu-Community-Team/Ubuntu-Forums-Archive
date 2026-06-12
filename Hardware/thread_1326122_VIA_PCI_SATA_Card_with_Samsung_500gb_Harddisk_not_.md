---
title: "VIA PCI SATA Card with Samsung 500gb Harddisk not booting"
date: 2009-11-14
forum: Hardware
---

### Post by ridowan007 on 2009-11-14
Today I bought a new Pci Sata Controller Card with a Samsung 500 gb Sata hard disk. My motherboard is intel D845EPI (845 chipset) wich has no Sata port. So I bought the pci sata controller. But after I set up all my Kubuntu installed on old Maxator 40 gb harddisk don't boot. When I switch off "quite splash" Option in grub then I saw there are telling many errors. But when I only removed the new Sata Harddisk(Not the pci card) Kubuntu normally boot. I am helpless. I don't know what the problem. Please somebody help. My PC is
CPU : Pentium 4 2.00A GHz
Memory : 1.25 GB
Motherboard : Intal D845EPI
New PCI Sata Controller card : Any Chinese company with Via 6421 chipset.(lspci result "02:01.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)")
New Harddisk : Samsung 500 GB Sata harddisk.

---

### Post by MatthewMetzger on 2009-11-16
The SATA card that you have doesn't seem to be able to boot. It'll work fine as extra storage, but the boot drive has to be connected to the motherboard.

If you find a way to boot a drive from this card, I'd like to know. Thanks.

---

### Post by valentt on 2009-11-29
I found the answer on how to make this VIA VT6421 card work on Ubuntu:

sudo modprobe sata_via

more details on my blog:
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)

---

