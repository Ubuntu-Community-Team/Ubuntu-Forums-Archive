---
title: "DVD burner: speed at 0.1X"
date: 2010-02-04
forum: Hardware
---

### Post by JB's on 2010-02-04
hello,
I  have a problem with the DVD burner and I can not solve ..
Reading is good, but not exceed 0.1 X burn speed.

> DVD Burner: LG gh22ns50 (manual  [http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS30&initialTab=warranty](http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS30&initialTab=warranty)  #)

> Motherboard: Asus M3N78-VM (this is the manual:  [http://dlcdnet.asus.com/pub/ASUS/mb/socketAM2/M3N78-VM/E4425_M3N78-VM_V4-manual.zip](http://dlcdnet.asus.com/pub/ASUS/mb/socketAM2/M3N78-VM/E4425_M3N78-VM_V4-manual.zip))

> I have Kernel 2.6.31-18-generic

I configured the BIOS  IDE mode

What  could be the problem? DVD burner is not supported?

Thanks in  advance, and excuse my bad english...  :oops:

---

### Post by momsab on 2010-02-04
short answer: try K3B

---

### Post by JB's on 2010-02-04
Hi,
I tried K3b,Brasero,GnomeBacker and Infrarecorder (wine)
Not work..  :icon_frown:

---

### Post by JB's on 2010-02-05
```
dmesg | grep scsi.\ :
```Results:
```
[    1.101542] scsi0 : ahci
[    1.101609] scsi1 : ahci
[    1.101649] scsi2 : ahci
[    1.101686] scsi3 : ahci
[    1.101723] scsi4 : ahci
[    1.101761] scsi5 : ahci
[    1.102104] scsi6 : pata_amd
[    1.102142] scsi7 : pata_amd
[   10.776439] scsi8 : SCSI emulation for USB Mass Storage devices

```This means that the first 6 SATA channels are controlled by AHCI.
Can you tell me how to configure to control the channel 5 (for example) in pata_amd?
Could be the solution.. ..or not? 


Someone  has this motherboard? :)

EDIT:  fixed!  Updated to Lucid 10.04 and the dvd burner works!

---

