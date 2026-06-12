---
title: "How to force an m.2 sata drive to stay as SDA"
date: 2016-12-22
forum: Hardware
---

### Post by Sean_Ooley on 2016-12-22
I have the following setup:

1 500 GB M.2 SATA drive
2 3 TB standard platter SATA drives
1 1 TB standard platter SATA drive
1 500 GB standard platter SATA drives

If I unplug all the standard platter drives and go about installing Ubuntu or one of the derivatives, the M.2 gets designated as SDA and the partitions are SDA1, SDA2, etc...
If I then plug the other drives in, the two 3 TB drives are then SDA and SDB, the 1 TB is SDC, the 500 GB is SDD and the M.2 drive is now SDE.

What I want to know is this: How can I make Ubuntu recognize the M.2 drive as SDA and the other drives SDB, SDC and so on.

I know, in the great scheme of things, that the designation of the drive doesn't mean a whole lot since GRUB is booting things properly, but it still irks me and I like GParted and lsblk to show them in my order.

Just in case it's necessary to know, I have an ASUS Maximus VIII Hero Alpha Motherboard with UEFI bios and the settings to use UEFI instead of legacy.

---

### Post by kpatz on 2016-12-22
Generally the sda, sdb etc. are in order by the SATA ports, so look at your motherboard, and plug the SSD into the 1st SATA port, then whatever you want to be sdb into the 2nd port, etc.

---

### Post by Sean_Ooley on 2016-12-22
An M.2 Sata drive doesn't plug into sata ports. It is a small little card that plugs directly into the motherboard. [Samsung 850 EVO M.2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820147399")
[IMG]http://images10.newegg.com/ProductImage/20-147-399-07.jpg[/IMG]

---

### Post by QIII on 2016-12-22
Hello!

Depending on the mobo, an M.2 may go though the SATA bus, the PCIe bus, what have you.

In any case, the devices will be enumerated by the mobo and that information passed to the OS which will call them sda, sdb, etc.  That's why we have gone to using UUIDs for mounting in fstab, etc.

I wouldn't get wrapped around the axle over an arbitrary enumeration so long as you can identify the devices.

---

### Post by MartyBuntu on 2016-12-22
> **Sean_Ooley said:**
> An M.2 Sata drive doesn't plug into sata ports.

PCI-E slots on the motherboard may be SATA assignable in the BIOS/UEFI...

---

### Post by Keith_Helms on 2016-12-22
Try out different motherboards until you find one that reports the drives to the OS in the order that you want.

---

