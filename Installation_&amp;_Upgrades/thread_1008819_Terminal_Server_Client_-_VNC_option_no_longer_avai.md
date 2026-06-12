---
title: "Terminal Server Client - VNC option no longer available"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2008-12-11
In Ubuntu 6.06 I used to use VNC as it was part of the default installation.

When I upgraded to Ubuntu 8.04 (fresh install actually), the VNC option ("protocol") is no longer available. In fact, out of the 4 options listed (RDPv5, VNC, XDMCP, ICA), only RDPv5 is available. The rest are grayed out.

How do I get VNC to be not grayed out on Terminal Server Client?

Thanks!

---

### Post by xp_newbie on 2008-12-16
:shock:

---

### Post by xp_newbie on 2008-12-16
OK - got it. Here is the undocumented secret:

No need to re-enable it, nor install anything else to be able to access the old VNC servers out there.

Instead, there is a default Remote Desktop Viewer that is compatible with those VNC servers, called **[COLOR="Navy"]vinagre[/COLOR]**.

Use port 5000.

---

### Post by heatpumpcontrol on 2010-05-19
sudo apt-get install xtightvncviewer xvnc4viewer

---

