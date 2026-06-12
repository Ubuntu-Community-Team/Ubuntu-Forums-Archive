---
title: "Why is my xorg.conf empty?"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by David Jenkins on 2008-12-21
I have just loaded 8.10 alternate onto an aged Toshiba Satellite laptop.  As usual, the Ubuntu install didn't work out the correct resolution for the screen, so I tried to open xorg.conf to apply the usual fix (changing 24-bit colour to 16-bit), which has always worked in the past.

Unfortunately, this time /etc/X11/xorg.conf is an empty file - no text in it whatsoever.

Have things changed?  Was there an install error? 

Any clues would be appreciated!

cheers,
David

---

### Post by PmDematagoda on 2008-12-21
The X-Server in Intrepid and above is such that it makes as little use of xorg.conf as possible, in some cases(like yours) the xorg.conf file can be empty. But you can create and use an xorg.conf file. To do so, try booting Ubuntu in Recovery Mode and selecting xfix, then see if an xorg.conf file is created.

---

### Post by David Jenkins on 2008-12-21
Ahh - I see. Is there a better way to set the colour to 16-bit?  It would be nicer to stick to the original intent rather than revert to the bad old ways!

---

### Post by David Jenkins on 2008-12-21
I'll answer my own question - I'll explore some of the official ideas mentioned in [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution").

cheers! :D

David

---

