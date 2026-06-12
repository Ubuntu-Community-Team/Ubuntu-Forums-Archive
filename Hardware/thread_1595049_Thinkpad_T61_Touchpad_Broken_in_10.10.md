---
title: "Thinkpad T61 Touchpad Broken in 10.10"
date: 2010-10-12
forum: Hardware
---

### Post by ghempton on 2010-10-12
Upgraded to 10.10. Touchpad works before I log in, after logging in it stops working. It worked fine for a week after I upgraded.

Touchpad works fine in Windows 7 (dual boot).

The trackpoint works fine, just not the touchpad.

Any ideas?

---

### Post by dgilbert on 2010-10-27
> **ghempton said:**
> Upgraded to 10.10. Touchpad works before I log in, after logging in it stops working. It worked fine for a week after I upgraded.

Touchpad works fine in Windows 7 (dual boot).

The trackpoint works fine, just not the touchpad.

Any ideas?

You might try Fn-F8 . If that fails go to this directory /usr/share/X11/xorg.conf.d and look for a file called 50-synaptics.conf . If it has a line in it containing "disable" try deleting that line. It seems you need to log out and back in again before that takes effect. [Where is the Ubuntu doco about this? This stuff used to be in /etc/X11 ...]

BTW Looking in /var/log/Xorg.0.log might help. [Ubuntu: why is the X capitalized?]

---

