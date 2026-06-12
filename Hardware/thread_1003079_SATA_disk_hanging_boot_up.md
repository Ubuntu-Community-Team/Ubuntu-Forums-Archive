---
title: "SATA disk hanging boot up?"
date: 2008-12-05
forum: Hardware
---

### Post by meanmrmustard on 2008-12-05
This isn't specifically an Ubuntu question but...
I'd like to install Ibex on a new Seagate 1Tb SATA drive but I can't get past the POST. It gets to recognizing the Silicon Image SATA card (PCI) and the hard disk and then simply hangs.

I have two other SATA drives in the machine (not connected at the same time as when the 1TB drive is connected), besides being smaller (500Gb each) the only difference is that they both have the molex (IDE) connector for power where the new drive has the SATA type power connector. I can't imagine that it would make any difference but....
I'm stumped.
For the record, the PCI card is restricted to 1.5 Gb/sec transfer rate and hard disk still has the jumper on to reflect that.
The other two SATA drives work in this machine with no problem.

I've searched the BIOS for some setting but haven't found anything relevant.

What am I missing?

Mobo; A7V8X-X
Proc: AMD Athlon XP 2700+ 
Video: Nvidia FX 5200
Silicon Image Sil 3114 SATARaid PCI card
2 x 500 MB RAM chips

---

### Post by Therion on 2008-12-05
Go into your BIOS setup menu and look at the drive settings in: 

Integrated Peripherals/SATA Devices Configuration 

Change the drive's default setting from **SATA** to **IDE**.

Save the changes, continue with booting and attempt a new install.

---

### Post by meanmrmustard on 2008-12-06
> **Therion said:**
> Go into your BIOS setup menu and look at the drive settings in: 

Integrated Peripherals/SATA Devices Configuration 




There is no SATA setting available.

The only choice there is allows for changing the type of IDE device under each of Primary/Secondary Master/Slave drives. The choices are:
None
Auto
User Type HDD
CD-Rom
LS-120
Zip
MO
Other Atapi Device

My other machine built on an ASUS  A8N-VM CSM does show First SATA Second SATA, etc. in the BIOS settings since it has an onboard SATA connector.

---

### Post by meanmrmustard on 2008-12-06
Edit:
This Mobo also doesn't allow choosing SATA in the boot order since it doesn't support SATA natively.

---

### Post by meanmrmustard on 2008-12-07
~~Bump~~

I've tested all four connectors on the SATA card - all get the same result - no go.

I've plugged in the other SATA drives (WD 500GB) to the problematic machine and the it boots and allows me into the card's BIOS setup without a problem.

I've also put the Seagate discs in another machine (with integrated SATA ports) and it installs and boots as it should.

I guess I'll get another SATA card to see if that will make a difference.

Any other ideas?

thanks

---

