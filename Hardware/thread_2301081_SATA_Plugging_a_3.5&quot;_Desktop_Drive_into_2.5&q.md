---
title: "SATA: Plugging a 3.5&quot; Desktop Drive into 2.5&quot; Laptop Drive Bay"
date: 2015-10-30
forum: Hardware
---

### Post by AnotherBrian on 2015-10-30
**Question 1:**  Can I use a sata/power extension cable to boot the laptop  off an old 3.5" sata disk drive?  So the laptop would provide power to the hard drive. My concern would be that the power supply of the laptop is inadequate for the physically large hard drive and I might fry the laptop. 
[B]
Question 2:[/B]  I have a USB/SATA adaptor.  The unit consists of two components, the power supply for the disk and the sata/usb adapter.  Can I use the power supply to power up the 3.5" inch drive and a sata extension cable to  connect the 3.5" drive directly into the laptop.  The concern here is that the hard drive is powered from an external source than the sata connection in which case the two interfaces (sata and sata  power supply)  will not share a common ground.  I am thinking this would not be a problem but perhaps the specs for these require such a common ground.  Also the laptop (BIOS?) might consider it an error condition when it sees a drive on the sata interface but no power is being drawn from the laptop. 

OK - why would someone want to do this when one can boot from the usb/sata adaptor.  Some of the disk functions are not accessable through a usb/sata adapter - case in point SMART Data disk health info  is not accessable via usb/sata adapter. Also one may not have a usb/sata adaptor.

---

### Post by sudodus on 2015-10-30
I suggest that you use the power supply of the USB/SATA adapter instead of risking to fry the laptop's power supply.

In the same situation I would use a SATA cable to connect and get better speed and other features. But your concern about common ground is relevant. You should connect the power to the computer and the adapter very close to each other and avoid large loops of the wiring to avoid induction currents.

---

