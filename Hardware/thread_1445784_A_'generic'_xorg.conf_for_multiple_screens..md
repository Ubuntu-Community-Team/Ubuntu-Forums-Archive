---
title: "A 'generic' xorg.conf for multiple screens."
date: 2010-04-03
forum: Hardware
---

### Post by dE_logics on 2010-04-03
Initially X does not use xorg.conf. So suppose I have a certain monitor installed with the system, then X will be set in accordance to that monitor.

If I change the monitor after a reboot, what problems will I face?...will X work properly? How does X handle this situation?

Suppose I did generate an xorg.conf, then the monitor, modes and screen section will be specified to the specific monitor in use. The reason why I generated this xorg.conf is cause I wanted some tuning with the dri section, or input device section etc... thus I need this specific xorg.conf. Now with these setting in xorg.conf, I change my monitor...this will give problems but I do not want any problems without modification to xorg.conf (i.e without again running Xorg -config). What should I do? All I want is a set of options in xorg.conf such that it's it's generic for most monitors (not for the garaphs hardware).

Or I want to setup the system on using monitor, and actually use it for a different monitor without the hazel of reconfiguring.

---

### Post by diesch on 2010-04-03
Only include the things you want to modify in your *xorg.conf* so anything else will still be autodetected by X.org

See [https://wiki.ubuntu.com/X/Config/](https://wiki.ubuntu.com/X/Config/) for some docs.

---

### Post by dE_logics on 2010-04-03
Ok, thanks.

---

