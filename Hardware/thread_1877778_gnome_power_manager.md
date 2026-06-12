---
title: "gnome power manager"
date: 2011-11-08
forum: Hardware
---

### Post by HalB2 on 2011-11-08
Yesterday, after many months of near error free use, I was unable to log into Ubuntu.(10.04 LTS installed using WUBI) It  displayed the message: "the configuration defaults for GNOME Power  Manager have not been installed correctly. Please contact your computer  administrator".  I was able to log on as root and after much experimenting  and no success I came up with this bright idea :confused:: **apt-get remove gnome-power-manager **followed by **apt-get install gnome-power-manager.** First part went well:grin:.
However...the **install **failed with many messages basically saying that _unable to resolve any ubuntu archive sites_.  I cannot remember exact wording but seems to me it was referring to an  IP/DNS problem.  Anyway...I'm stuck. Any/all help appreciated. Hal

---

### Post by MoreOrLess on 2011-11-08
First, you should remove the residual configuration because you wanted to apt-get purge, not just remove (look in Synaptic).

See if the package is in your /var/cache/apt/archives folder and dpkg -i to install it. If not, find a way to get it on your system and install it.

---

