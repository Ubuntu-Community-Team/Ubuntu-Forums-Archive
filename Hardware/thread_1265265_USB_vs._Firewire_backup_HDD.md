---
title: "USB vs. Firewire backup HDD"
date: 2009-09-13
forum: Hardware
---

### Post by fela on 2009-09-13
We're looking into getting an external 1TB HDD to backup all the data that's currently on our server and some clients but not currently backed up (on my desktop machine I recently had a HDD disaster and am more aware of the need to backup).

The dilemma is this: I know that USB 2.0 is much slower than Firewire 400, the server has USB 2.0 via its onboard chipset and Firewire 400 via a PCI card. It also has a SATA port that can be accessed externally (still internal SATA though, not eSATA), and I also know that this is way faster than either USB or firewire (I'd have to get an eSATA case and a SATA to eSATA converter cable though).

But USB drives are a lot cheaper than USB+Firewire drives and I'm wondering if getting a USB-only drive would be alright. I don't mind leaving it overnight backing everything up straight from the server, but I would like be able to put files onto it from other computers at reasonable speeds (not overnight). We have two client machines that support Firewire out of 5, but these are the only ones that have a considerable amount of data on them (aside from the server of course). So if the case did support firewire it would definitely be used to its full extent.

**The bottom line is, do you think it's worth it to get a firewire+usb drive, or should I just go with the cheaper option: USB only?**

---

### Post by Bucky Ball on 2009-09-13
Firewire faster, eSATA fastest if you have the port.

Don't get confused with speeds; firewire is a more constant speed, USB is speed in bursts (simplified version).

---

### Post by fela on 2009-09-13
> **Bucky Ball said:**
> Firewire faster, eSATA fastest if you have the port.

Don't get confused with speeds; firewire is a more constant speed, USB is speed in bursts (simplified version).

I think I'm going to go with a USB drive as I know that firewire has a big speed advantage, but:

1) Speed isn't of utmost importance as it's just a backup drive, I can leave it overnight backing up if I have to;

2) I don't think the advantage would be worth £40.

So yeah, USB only it is :( Oh well :)

---

### Post by rob-ward on 2009-09-13
The firewire interface being faster then the USB interface will have little to no effect on the speed you access the drive, this is because even the USB interface has 480mbps or 60Meg per second data throughput, most cheap drive arn't any faster than this so just stick to USB as it is then easier to attach to another computer later as USB ports are standard firewire isn't.

---

### Post by fela on 2009-09-13
> **rob-ward said:**
> The firewire interface being faster then the USB interface will have little to no effect on the speed you access the drive, this is because even the USB interface has 480mbps or 60Meg per second data throughput, most cheap drive arn't any faster than this so just stick to USB as it is then easier to attach to another computer later as USB ports are standard firewire isn't.

Actually the actual speed of USB is way slower than that. If it actually delivered 480Mb/s throughput then it would be faster than firewire.

---

### Post by rob-ward on 2009-09-13
True there is an overhead but I have achieved about 35-40 throughput in the past and still that competes with the speed of cheap drives, if you want faster you shove them instide you computer :-) well until usb3 is released(next year???)

---

### Post by Whiffle on 2009-09-13
I regularly copy at 25-30mb/s to my USB drive, not sure what a firewire would do.

---

### Post by fela on 2009-09-13
> **Whiffle said:**
> I regularly copy at 25-30mb/s to my USB drive, not sure what a firewire would do.

I must have an issue with USB then, as I get far worse speeds than that...

But anyway, I've now ordered a USB-only Western Digital 1TB from amazon. Even if it does have bad transfer rates, we've decided it's only gonna be connected to the server and will do regular overnight backups. I'll have to make a cron script backup any changes from the server to the harddisk...shouldn't be too difficult :)

---

