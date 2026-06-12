---
title: "Checking proper hardware installation/drivers. How do I get my SAS card working?"
date: 2008-10-27
forum: Hardware
---

### Post by ohboyotero on 2008-10-27
Heyo :)

I'm  busy trying to put an SAS card in my server so I can attach an external disk array. I'm eventually trying to set up as a RAID 5 array and use it as network attached storage for my house...but that's a long way away.

Specifically, I'm using:

Ubuntu: Server 8.04
SAS card: LSI SAS 3800x (PCI) [product description]("http://www.lsi.com/storage_home/products_home/host_bus_adapters/sas_hbas/lsisas3800x/index.html?remote=1&locale=EN")

So, after searching for info on installing new hardware and getting nothing but "pop it in and it should work," I popped in the PCI SAS card, attached my disk array to it, and rebooted the machine.

I know next to nothing about hardware/drivers in Linux/Ubuntu, so naturally, after a quick look in the /dev folder revealed no new disks or otherwise eye-grabbing devices, I was stumped as to how to figure out if

a) the hardware is correctly installed,
b) the appropriate drivers have been obtained (and if they work)
c) if drivers haven't been installed, how do I go about finding them and installing manually?
d) how to actually interact with the new hardware (in the general case; here it should be as easy as new sdX hard drives showing up in /dev)

Any ideas? I can't exactly set up RAID if I don't know how to access the external drives :D

Thanks for any and all input. If I left out some vital info, let me know and I'll include it. If procuring that info requires knowledge a noob does not likely have, I'd also appreciate a word on how to do so.

---

### Post by ohboyotero on 2008-10-28
I should mention that I have run lspci and the SAS card has NOT been detected.

---

