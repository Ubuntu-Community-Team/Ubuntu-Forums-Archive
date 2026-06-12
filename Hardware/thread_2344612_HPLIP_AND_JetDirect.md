---
title: "HPLIP AND JetDirect"
date: 2016-11-26
forum: Hardware
---

### Post by charlie_bravo2 on 2016-11-26
So, I screwed up and bought a non-wireless HP printer from Woot.  I was comparing two models, one with and one without, and then bought the wrong one.  Figured I could remedy this by getting an external JetDirect device from HP, connect it to my network, and then use HPLIP to configure my connection to the printer.  No luck.

The Details:
OS:  Xubuntu 16.04, fully up to date
JetDirect: HP Wireless G USB Print Server 2101nw
Printer: Color Laser Jet Pro M452dn
HPLIP 3.16.10

I can connect to the printer via USB and print, which tells me sufficient drivers are installed on the Xubuntu box to allow it to print.  I was able to configure the 2101 to connect to my home wireless network using my MacBook Pro.  Having tried to configure the connection with HPLIP, there's a option to connect via USB to a Printer you intend to connect to wirelessly later.  Plugging into the printer fails to allow configuration as the printer itself cannot do wireless.  Connecting directly to the 2101 fails for reasons I cannot determine, regardless of it being connected to the printer or not.  I have CUPS also installed and current.  Additionally, I have ensured I have the the PPD.GZ files for the printer I am trying to install.

My questions are:
1. Can this set-up be made to work, the JetDirect device connecting the printer to the network, and thus the printer then being accessible to the computers in the house, one Xubuntu laptop, one MacBook Pro?
2. Can someone provide a step by set set of instructions for this setup?

---

