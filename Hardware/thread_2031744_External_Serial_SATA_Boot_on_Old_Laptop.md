---
title: "External Serial SATA Boot on Old Laptop"
date: 2012-07-22
forum: Hardware
---

### Post by wadedesk on 2012-07-22
I have an old Compaq P3 laptop that still gives me good service.  In addition to the PATA drive bay, it has a multi-bay for for CD-ROM, Floppy, Zip and second Hard Drive.
I've been able to locate a SATA hard drive adapter that fits the multi-bay.  Rather than install a large SATA internal 2.5" drive, I would like to put a SATA to eSATA cable in this adapter.
The laptop only has USB 1.1 built-in and I'm not able to boot an external hard drive from the CF slot when I use install USB 2.0 or eSATA adapters in the CF slot.  However I should be able to boot an external hard drive off the multi-bay since it is configurable in BIOS.
It appears that I can plug-in a SATA cable to a 2.5 inch SATA drive.  I have a SATA to eSATA cable, so it appears that all I need is a gender changer for the cable.  Do I need a male-to-male changer or a female-to-female?  I'm not sure if the hard drive has a male or female connector?  But I need a cable that has a connector like a hard drive on one end and an eSATA connector on the other end.
To summarize, I have an hard drive holder to fit a Compaq multi-bay.  I want to install a SATA to eSATA cable in the bay to allow connection of an external hard drive instead of mounting an internal SATA Drive.  So what kind of cable do I need?  Where can I find it?
Sorry for the long post, but I want to be clear what and why I'm attempting this project.
Thanks in advance!

---

### Post by gordintoronto on 2012-07-22
I doubt very much that your laptop will support SATA. You need a PATA (IDE) hard drive.

---

### Post by wadedesk on 2012-07-23
The old P3 is my baby.  I already have replaced the internal PATA hard drive with a CF card adapter that has Lubuntu on it.  With Linux on a Flash card, I can use it as a netbook.

I have Windows XP installed to a PATA drive that mounts in the multi-bay.  I also have Xubuntu on a SATA drive that mounts in the multi-bay.  But I wanted to be able to boot to some of my 1-Tb external SATA drives.

I did a lot of digging around on eBay and I found a male-to-female SATA extension data cable that has exposed contacts on the female plug.  I then found a female SATA to female eSATA coupler.

When all the parts arrive, i plan on mounting the coupler in a hole that I make in the edge of a new SATA drive cage that fits in the multi-bay.  I then will plug the female SATA cable end in where the hard drive would attach and plug the male end into the coupler.

When I inset the new SATA drive cage in the multi-bay, it should give me a bootable eSATA port on my old p3 laptop.  Total cost for all the parts (so far) is less than $22.

I will post a follow-up after I get all the parts and test my project.

---

