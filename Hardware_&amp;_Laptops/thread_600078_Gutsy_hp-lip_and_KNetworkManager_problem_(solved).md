---
title: "Gutsy hp-lip and KNetworkManager problem (solved)"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by WayneSteenburg on 2007-11-01
Following the advice of others posts, I deleted my /etc/network/interfaces file to use the roaming mode of KNetworkManager.  It would seem that hp-setup and other hp-lip programs need use of this file (perhaps the loopback reference).  I've been having trouble all day with hp-setup.  When run it would never get to drawing the gui.  On a hunch I restored my backup interfaces file (always backup before deleting :))and hp-setup finally ran.  Just thought I'd add this to the forum in case someone else runs into this.  As a side note it would appear a better way to enable roaming on Gutsy is to just comment any lines referring to the interface in question in /etc/network/interfaces.

---

