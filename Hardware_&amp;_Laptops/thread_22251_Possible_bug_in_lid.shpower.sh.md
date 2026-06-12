---
title: "Possible bug in lid.sh/power.sh"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by shooz on 2005-03-26
Hey all --

Got Ubuntu running nicely on my Toshiba Satellite 2180CDT.  Right now the problem I'm dealing with is the screen not getting restored when the lid is closed.  The /etc/acpi/lid.sh is supposed to store the current vt in $LIDSTATE when closed, then restore it from $LIDSTATE when opened.  However, it does not seem to be restoring it properly.

It looks like something else is writing to $LIDSTATE (/var/lib/acpi-support/lidstate).  Right now this file contains AC.  When I unplug the power cord it changes to BATTERY.  I believe one of the other acpi scripts are accidentally putting the power cord state in this file which is clobbering the saved VT number from lid.sh.

Anyone else see this problem?

cheers,
shooz

---

### Post by jdong on 2005-03-26
Please file a bug with Ubuntu.

---

