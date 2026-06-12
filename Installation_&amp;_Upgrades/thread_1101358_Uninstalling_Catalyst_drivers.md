---
title: "Uninstalling Catalyst drivers"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by vsen123 on 2009-03-20
Hi,
I installed Catalyst 9.1 manually using the wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way")
I want to switch to the latest 9.3 driver or give the new open source drivers a try.How do I uninstall the Catalyst 9.1 drivers(when they are installed manually by .deb packages??).

---

### Post by Mark Phelps on 2009-03-20
IF you installed using the script, you will have the file fglrx-uninstall.sh for uninstalling the ATI drivers.

To do that, run "sudo sh /usr/share/ati/fglrx-uninstall.sh" in a terminal.

When done, run "fglrxinfo" from a terminal and it should say it's not installed.

BTW, I didn't see the Catalyst 9.3 drivers for Linux; the drivers page only showed the drivers for Windows at 9.3.  The linux drivers were still shown at 9.2.

Also, be aware that if you're running a R300 or R500 series card, you're wasting your time upgrading because AMD is ending support in the proprietry drivers for those cards with version 9.2.  Version 9.3 will only support R600, R700 series and newer.

---

### Post by ssri on 2009-03-21
> **Mark Phelps said:**
> IF you installed using the script, you will have the file fglrx-uninstall.sh for uninstalling the ATI drivers.

To do that, run "sudo sh /usr/share/ati/fglrx-uninstall.sh" in a terminal.

When done, run "fglrxinfo" from a terminal and it should say it's not installed.

BTW, I didn't see the Catalyst 9.3 drivers for Linux; the drivers page only showed the drivers for Windows at 9.3.  The linux drivers were still shown at 9.2.

Also, be aware that if you're running a R300 or R500 series card, you're wasting your time upgrading because AMD is ending support in the proprietry drivers for those cards with version 9.2.  Version 9.3 will only support R600, R700 series and newer.

Wrong, Catalyst 9.4 will be the first release to drop legacy support for R300/400/500 cards.

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

---

