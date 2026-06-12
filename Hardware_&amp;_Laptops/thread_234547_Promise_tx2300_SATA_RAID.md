---
title: "Promise tx2300 SATA RAID"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by jzimmerman on 2006-08-11
I have a Promise tx2300 SATA RAID card that is not detected.

I would like to run my drives in a mirror configuration.

The Promise support site only posts a partial source driver for 2.4 kernels.

Does anyone have this card working under Ubuntu (or SuSE, or any other 2.6 kernel) in any configuration, RAID or otherwise?

I would be interested in knowing what needed to be done to get it working.  Even if it is not in RAID mode, I can at least setup software RAID.

Thanks

---

### Post by nullspace on 2006-10-26
I also have this problem. I have tried edgy alternative and standard disks and neither detect the card reguardless if I setup a hardware raid or not. any help please

---

### Post by jzimmerman on 2006-10-26
I ended up relacing the card with one from HighPoint.  Everything works now.  Promise "eSupport" was very unhelpful (no response) and  (customer service) didn't seem to understand what a "kernel" was.

---

### Post by hkgonra on 2006-10-26
> **jzimmerman said:**
> I ended up relacing the card with one from HighPoint.  Everything works now.  Promise "eSupport" was very unhelpful (no response) and  (customer service) didn't seem to understand what a "kernel" was.

What highpoint card did you get ? I have 3 high-point Raid cards and have had MASSIVE problems getting them to run on any version of linux.

---

### Post by nullspace on 2006-10-26
bump

---

### Post by dcastellani on 2007-04-12
Anyone ever get the Promise TX2300 controller to work in ubuntu?

---

### Post by jzimmerman on 2007-04-29
> **hkgonra said:**
> What highpoint card did you get ? I have 3 high-point Raid cards and have had MASSIVE problems getting them to run on any version of linux.

Sorry for not replying sooner.  I am not very active on the boards.

 HighPoint RocketRAID 1640 PCI SATA Controller Card RAID 0/1/10 JBOD

I bought it from Newegg [here -->]("http://www.newegg.com/Product/Product.asp?Item=N82E16816115015")

I have had it running software raid and just recently upgraded the machine to Feisty.  Everything is working fine.

---

### Post by zer0fill on 2007-06-26
Anyone still trying to get the RocketRaid 1640 or any RAID controller using the HPT374 chipset, check out [http://stefan.freyr.org/?page_id=6](http://stefan.freyr.org/?page_id=6) for an easy guide to get yourself up and running in about 10-15 minutes. It was a LOT easier than I expected.

---

### Post by Feohnelats on 2007-07-18
I just installed a Promise TX2300 SATA RAID in my server. I can see both my disks attached to the controller without doing anything extra apart from revering to them in the BIOS. Unfortunately I do not have the feeling it is quite RAID 1 as I tried to setup in the controllers BIOS.

Cheers.

---

### Post by igknighted on 2008-03-20
For some reason Ubuntu does not recognize this card.  Well... it will see the drives individually, but not use the RAID.  Suse, Mandriva, Fedora and CentOS all see the array perfectly, so I think it is a Ubuntu or Debian specific bug.

Note: I am using 2 80gb disks in raid 1

---

