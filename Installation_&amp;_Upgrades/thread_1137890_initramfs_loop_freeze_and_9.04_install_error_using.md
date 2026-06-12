---
title: "initramfs loop freeze and 9.04 install error using Wubi"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by ianshortreed on 2009-04-26
I am installing a clean 9.04 AMD 64 bit.iso using Wubi onto Windows XP SP3 on a DELL Vostra with 2 GIGS RAM and the installer hangs when the initramfs tools pops up about 95% of the way through the installation where it gets into a loop and never completes the install showing the same 95% complete dialog forever. Done this 3 times so far just for a little self torture on a Sunday.

Does anybody have any experience getting around the same issue?:confused:

---

### Post by ianshortreed on 2009-05-03
I am going to answer my own question here which will hopefully help others who might be as silly as myself when doing a clean install. 

The Ubuntu installer requires that you have a wired Internet connection to finish the 9.0.4  install. If you're  thinking that a wireless or wired PPP over Ethernet connection will work, you will end up at this loop at the end of the install showing 95% installation complete and the initramfs tools running dialog in a terminal loop.

Bottom line: You need to have a live wired DHCP over Ethernet connection in order for the install to finish and avoid this loop.

Engineering note: For future releases, it might be kinder to throw up an alert after running a gestalt at the beginning of the install sequence  to check if there is a DHCP Ethernet connection and reminding the user that that connection must be over DHCP not PPP over Ethernet which requires a username and password to open a connection or Wireless since the Broadcom or other wireless drivers are not activated until after the install is finished.

The good news: once installed, life is very good, indeed!

---

