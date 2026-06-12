---
title: "Quit option missing from System menu after upgrade"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by deangl on 2009-10-23
Hi,

After upgrading to 9.04 the System menu on the desktop no longer contains the quit options.  Consequently, I now have now shutdown/reboot option buttons accordingly.

I tried dpkg reconfigure on gdm, and rebooted with no apparent change.

This is frustrating that something so simple and necessary would be broken on a basic upgrade.  What am I doing wrong?

Any help would be appreciated.

Thanks,
Dale
:confused:

---

### Post by restart on 2009-11-15
Up! Anybody?

---

### Post by coffeecat on 2009-11-15
It is not broken - it is changed. Far right of top panel should be your login name and a switch logo. Click that and you have all the log out, suspend, shutdown, etc options. If by chance that has disappeared, just add the 'Indicator-Applet-Session' applet to your panel.

---

### Post by deangl on 2009-11-16
Thank you so much.  I appreciate the response/help.  Have a great day.

---

