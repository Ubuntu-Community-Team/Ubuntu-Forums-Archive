---
title: "[SOLVED] quadro FX1600 and Maya freeze"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by luckyluca on 2008-02-25
Hello,

I'm running maya 8.5 64bit on my dell m6300 laptop with quadro fx1600, using the latest envy drivers 169.09.

Maya freezes sometimes and Houdini keeps crashing.  I've also tried by editing the /etc/X11/xorg.conf and disabling the composite line with no success.

I would be willing to give older drivers a go but every time I try either the 96.43.01or the 71.86.01ubuntu only starts in low graphics mode. The only working driver for me is the 169.09.

Has anybody encountered similar problems, is there a common workaround or should I head back to windowsXP for better stability (!!) ? :(

Thanks
Luca

---

### Post by luckyluca on 2008-02-26
Solved by adding the CIDoverlay line to the xorg.conf file

---

