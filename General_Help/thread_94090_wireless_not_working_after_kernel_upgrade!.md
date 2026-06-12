---
title: "wireless not working after kernel upgrade!"
date: 2005-11-23
forum: General Help
---

### Post by termite on 2005-11-23
I just updated my kernel from 2.6.12-10-386 to 2.6.12-10-686.  On reboot, the system failed to detect/install my wireless card.  It works fine on the 386 kernel.  I'm running on a 1.4ghz celeron Toshiba laptop with an AR5212 wireless card.

Ideas?

---

### Post by termite on 2005-11-23
<bump>

Anyone?

some more info: in device manager, it shows the card plus 'networking interface' in 386, but without the latter in 686.

---

### Post by termite on 2005-11-23
<bump again>

surely someone knows what the heck is going on?  other people seem to be having trouble with this kernel update...

---

### Post by termite on 2005-11-23
ok, some progress:
/lib/modules/2.6.12-10-386 has a madwifi directory with the ath_pci.ko driver in it.
/lib/modules/2.6.12-10-686 has no madwifi directory whatsoever.

So...how do I install madwifi on the 686 installation given that I have no internet connection on it?  What would I do from there?

---

### Post by termite on 2005-11-23
turns out I needed the restricted package.  Installed it from Synaptic in the 386 installation and rebooted to 686.  Everything works.

---

