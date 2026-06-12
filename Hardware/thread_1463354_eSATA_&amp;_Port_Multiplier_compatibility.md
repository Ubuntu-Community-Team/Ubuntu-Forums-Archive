---
title: "eSATA &amp; Port Multiplier compatibility"
date: 2010-04-26
forum: Hardware
---

### Post by Oatworm on 2010-04-26
I have an eSATA connected hard drive enclosure that uses a pair of port multipliers to connect four hard drives each to one eSATA cable, with two such banks on my system.  This enclosure is used for backups.  The manufacturer of the system gave me an SiI 3124 PCI-to-eSATA adapter.  

The good news is that the open source sata_sil driver does allow my system, currently running the Ubuntu 10.04 release candidate, to view one hard drive from each bank.  However, it would appear that the driver does not allow the card to speak to the port multiplier correctly.  There is a driver for the SiI 3124 card provided by the manufacturer, but it dates back to the 2.6.16 kernel and is consequently not compatible with 2.6.24+ kernels.  The Windows driver does allow the machine to view all of the drives in the enclosure simultaneously if I boot into Windows.

Here's my question:  Is there either a way to use ndiswrapper to use the Windows driver for my eSATA-to-PCI card, or is there a better supported eSATA card out there that handles SATA port multipliers sanely that I can use with either up-to-date driver support from the manufacturer or with open source driver support?

Thanks in advance.  Google has not been my friend so far.

---

