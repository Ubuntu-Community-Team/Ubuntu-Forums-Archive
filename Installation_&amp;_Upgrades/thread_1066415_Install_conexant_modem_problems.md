---
title: "Install conexant modem problems"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Numbnuts on 2009-02-10
I'm trying to install a Conexant PCI modem in Ubuntu 8 and it just won't happen. From scanModem the details are: -

************************************************************
Modem chipset  detected on
NAME="Communication controller: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem "
CLASS=0780
PCIDEV=14f1:2f50
SUBSYS=14f1:205f
IRQ=10
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  01:06.0
   0780 Communication controller: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem 
      Primary device ID:  14f1:2f50
 Support type needed or chipset:	hsfmodem
**********************************************************
 
We've installed Gnome PPP and installed the Conexant drivers from Linuxant as far as we can tell (because we can get a message that an install is an older version of one already installed!).

For some reason we cannot make the final link to /dev/modem. We also cannot get Gnome System Tools to install to see if that helps.

We think we're really close but after 3 days we've given up. Can someone please help?
Do we need to clean up the stuff we've been messing around with? (ie uninstall the driver)
Do we need to re-install Ubuntu from scratch?
Old versions of Ubuntu had a "Network Settings" application which we cannot find now. Do we need this? Should I use an old Ubuntu?

Help!

---

### Post by Numbnuts on 2009-02-15
I'm trying to install a Conexant PCI modem in Ubuntu 8 and it just won't happen. From scanModem the details are: -

************************************************** **********
Modem chipset detected on
NAME="Communication controller: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem "
CLASS=0780
PCIDEV=14f1:2f50
SUBSYS=14f1:205f
IRQ=10
IDENT=hsfmodem
Driver=hsfmodem-drivers

For candidate modem in: 01:06.0
0780 Communication controller: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem 
Primary device ID: 14f1:2f50
Support type needed or chipset: hsfmodem
************************************************** ********

We've installed Gnome PPP and installed the Conexant drivers from Linuxant as far as we can tell (because we can get a message that an install is an older version of one already installed!).

For some reason we cannot make the final link to /dev/modem. We also cannot get Gnome System Tools to install to see if that helps.

We think we're really close but after 3 days we've given up. Can someone please help?
Do we need to clean up the stuff we've been messing around with? (ie uninstall the driver)
Do we need to re-install Ubuntu from scratch?
Old versions of Ubuntu had a "Network Settings" application which we cannot find now. Do we need this? Should I use an old Ubuntu?

Help! It's no use to me without the internet and I can't afford Broadband.

---

### Post by bapoumba on 2009-02-15
Threads merged.

---

### Post by Numbnuts on 2009-02-15
Well thanks, but that doesn't help very much.

---

