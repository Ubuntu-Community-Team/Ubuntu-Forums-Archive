---
title: "Hot swapping drives."
date: 2013-11-06
forum: Hardware
---

### Post by alex120 on 2013-11-06
So I work as a tech and I'm trying to use an old server (IBM x3500 type 7977) to make a system to test/clone/data backup from multiple HDD.
The system has 3 x 4 Drive backplanes;
One connected by a Mini-SAS cable to motherboard port labeled SAS1 - This is the raid for my install.
One connected by a Mini-SAS cable to motherboard port labeled SATA - This is for drives to be worked on.
One connected with standard SATA cables to a PCIe Raid controller card - Also for drives to be worked on.

After poking around here and on Google I have found and installed scsitools however it only seems to work for the backplane connected to the PCIe controller.
Is there an alternative to scsitools or a better way to go about doing this?

---

### Post by alex120 on 2013-11-12
Nothing?

---

