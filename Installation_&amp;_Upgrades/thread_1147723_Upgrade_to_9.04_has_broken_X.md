---
title: "Upgrade to 9.04 has broken X"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Zymous on 2009-05-03
I tried an upgrade from 8.10 to 9.04 yesterday. It aborted with 19 minutes to go.

I booted to a recovery console and seemed to be able to complete the upgrade from the command line, but I am now unable to boot into X. The screen is frozen and is unresponsive to Alt-F1, Ctrl+Alt+Del etc

dpkg-reconfigure xserver-xorg doesn't make any difference and reverting to an old /etc/X11/xorg.conf slightly alters the image that the screen gets locked, but the system is still locked.

Is there anything that can be done to repair X or am I looking at a re-installation?

The machine is a [Toshiba Equium L100]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&DISC_MODEL=0&ACTION=PRINT_WITH_BACK&com.broadvision.session.new=Yes&PRODUCT_ID=119394") with an ATI Radeon Xpress 200M. The 9.04 Live CD runs without a problem.

-- 
Zym

---

### Post by Mark Phelps on 2009-05-05
The LiveCD most probably runs because it's using an open source video driver by default.  My guess is that you were running an ATI driver under 8.10 and that didn't get removed properly -- since 9.04 does not provide ATI driver support for your card.

Suggest you check out the following link to see if you can remove the remnants of the fglrx driver and install the open source driver in its place:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by dhbarnett on 2009-05-12
I had problems as well and had to remove the fglrx driver. Everything worked fine after that.

---

