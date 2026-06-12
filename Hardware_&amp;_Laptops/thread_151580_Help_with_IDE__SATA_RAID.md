---
title: "Help with IDE / SATA RAID"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by krakan on 2006-03-28
Right guys, firstly an apology for coming at this from a Windows angle, but that's the way I was raised and I'm trying to make amends now!

I'm installing a base (server) installation with the intention of making a Linux, Apache, PostgreSQL, PHP server for some software in development.

We're getting a depressing number of HDD failures in our Windows servers, which we're generally able to recover from, but our Linux experience (ie, actually having to fix things for ourselves) is rather limited and I'd rather avoid HDD problems having so great an effect in this situation.

The plan is to create a Mirrored RAID array for the system, and another for the data. I can create a software-based RAID volume for the data, and have done so in the past, but I've never actually installed Linux on what is essentially a non-existent volume. Those of you with Windows experience of this will know what I mean when I ask my question like this:

How do I press F6 on startup? How do I (assuming I can find a RAID adapter which has drivers available for it - open to help there, too!) load a driver for a RAID Adapter during the installation, and tell Linux to stick itself there? I've had a look through the How-To, but can't see anything directly relevant - if anyone else knows of an article that is, point me right there and I'll love you forever!

Any help greatly appreciated, mars bars offered to useful or amusing replies

---

### Post by gherikill on 2006-03-28
I would also like to know this.

---

### Post by tim.n9puz on 2006-03-30
I'm interested in this for an Ubuntu based file server as well. We use 3Ware Escalade 8006-2LP cards in our Windows server and have been very happy with them. 

I note that the 3Ware site says they do support Linux including source for drivers. Debian is specifically mentioned (among others) and in a search here on the forum someone indicates the card *should* be supported by the driver in the kernel.

My question is does anyone have first hand _successful_ experience using a RAID 0 card (mirroring) with Ubuntu? (3Ware or other.)

If the driver is supported in the kernel does the installer detect the card as a disk drive and the installation progresses as it would normally?

Tim

---

