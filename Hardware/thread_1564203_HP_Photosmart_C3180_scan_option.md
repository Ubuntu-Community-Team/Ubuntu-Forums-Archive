---
title: "HP Photosmart C3180 scan option?"
date: 2010-08-30
forum: Hardware
---

### Post by dimi_tris on 2010-08-30
hallo.
i have ubuntu 10.04.01 instalt. ubuntu recognize the printe with no problems. 
i cant  find an option for the printer to scan.
and the scan button on printer don't work either.
can you help?

---

### Post by magicfab on 2010-09-22
Hello

In System > Administration > Synaptic Package manager you need to install the hplip-gui package.

Then go to System > Preferences > HPLIP Toolbox and use the wizard. It may be needed to completely remove the printer using System > Administration > Printing before doing this, as HPLIP will install both the printer and scanner (and also provide access to card readers, ink levels, etc).

Your printer needs to be connected directly to your Ubuntu system, not shared via another networked computer.

---

