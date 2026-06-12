---
title: "eSATA problem SIL3512a on 9.04"
date: 2009-09-19
forum: Hardware
---

### Post by fmsafar on 2009-09-19
I attached a 1.5 TB drive that has USB2.0 and eSATA interfaces via the eSATA interface to a dual eSATA PCI Card (DeLOCK 70155) with a SIL3512a Chipset. The motherboard is an Asus CUV4X with a Pentium III at 600 MHz. The kernel is 2.6.28-15-generic.

When I was not able to install Ubuntu on that drive I  used an installation on the  internal IDE drive to find out what's wrong with the sATA. Using the USB interface I created a small ext2 partition on the drive and switched back to eSATA. Even on eSATA fsck reports everyhing OK. After writing an empty file fsck reports a wrong blockcount. After unmounting the partition the blockcount is OK.

Writing on the block level is no problem. I copied several partitions (about 150 GB) to the eSATA drive using dd. All filesystems are consistent and it is no problem to read the files. But it seems that the smallest change on the filesystem level leads to an inconsistent state.

What can I do to find out the reason of the problem? What additional information do I need to provide?

Thanks in advance for any help!
FMS

---

### Post by fmsafar on 2009-10-06
In between I noticed that my  "test" was nonsense. Nevertheless the Problem persits, even after updateing the fimware on the DeLOCK 70155 eSATA PCI card. So finally I tried a differnet dual eSATA PCI card from LaCie and the system works perfect with this card. The LaCie card has also the SIL3512a chipset and the same firmware (the new one which  I have loaded on the DeLOCK card by myself). Maybe the DeLOCK 70155 eSATA PCI card is working with Windows but accoring to my experiance it should not be used with Linux!

---

### Post by Francis 24/24 on 2010-08-10
Thanks for the information. I bought a Lacie esata dual port pci card without beeing sure it  was the one which worked for you, as Lacie does not mention the chip set of the card.
Fortunately, this card as shown there :
[http://www.lacie.com/us/products/product.htm?pid=11160](http://www.lacie.com/us/products/product.htm?pid=11160)
product reference : 130823
has the proper chipset as lspci shows :
02:0e.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

My configuration which works fine : 
ASUS Pundit R / Lacie esata dual port pci card 130823 / Hitachi sata II ?
in ICY BOX Model IB-319StUS2-B Interface USB 2.0 & eSATA
Ubuntu 10.04 Kernel 2.6.32-24-386

Cheers !

---

