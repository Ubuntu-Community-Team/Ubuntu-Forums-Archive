---
title: "&quot;$sudo dpkg-reconfigure -phigh xserver-xorg&quot; Not working"
date: 2008-08-16
forum: General Help
---

### Post by paquisimo on 2008-08-16
When I type this command I get this message and I do not know how to continue.

francisco@Calipso:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080816221345

Any help?

---

### Post by phidia on 2008-08-16
That message is just telling you that your present xorg.conf is going to be backed up (which you probably want to do anyway) and a new xorg.conf will be written.
I think you just press enter and let the dpkg command continue.

---

### Post by paquisimo on 2008-08-16
When I press enter it takes me back to the beginning. Other idea?

---

