---
title: "Prestigio nobile 157"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by sect2k on 2005-11-05
Has anyone got ubuntu working on prestigio nobile 157? 

I tried to install hoary and also tried to run both hoary and breezy livecds without success. Both install and live cd hang even before the installer starts, or maybe when staring the installer, in any case the screen goes blank and that's it.

Any ideas what might be wrong?

Cheers,
sect2k

---

### Post by sup on 2006-07-12
litle bit late, I suppose (although I started using Ubuntu on that laptop in november, actually).
You need to boot with parameter vga=771. As of Dapper, it is no longer needed, it only gives you better looking splash.

Everything work, except memorycard reader (it never will, some patents or something). Irda, modem, pcmcia and firewire unchecked but they shouuld work.

---

### Post by Vorian on 2006-07-13
> **sect2k said:**
> Has anyone got ubuntu working on prestigio nobile 157? 

I tried to install hoary and also tried to run both hoary and breezy livecds without success. Both install and live cd hang even before the installer starts, or maybe when staring the installer, in any case the screen goes blank and that's it.

Any ideas what might be wrong?

Cheers,
sect2k

Use an external monitor...

---

### Post by sup on 2006-07-17
BTW just found out how to get side buttons  to work - you need acerhk, load it witch autowlan=1 than mpa the  keys using xmodmap.conf and gconf/metacity/commands or with gnome keyboard shortcuts. However, the wireless button must not have assigned anything, atherwise switching wireless off and on will not work.

---

