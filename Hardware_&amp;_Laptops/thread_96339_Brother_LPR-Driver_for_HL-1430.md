---
title: "Brother LPR-Driver for HL-1430"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by geograf on 2005-11-28
I installed the Brother lpr-driver with:
dpkg -i --force-all hl1430lpr-1.1.2-1.i386.deb

as described on solutions.brother.com, also the cupswrapper-driver. The Printer himself works PERFECTLY with this combination on Ubuntu
(MUCH better than the recommended foomatic-hl1250, shiped with Ubuntu!)

But: A lot of errors occur during the installation of the lpr-driver. - It seems, the .deb needs /etc/init.d/lpd that's not there. 
Hereafter, the whole Synaptic-Update System is "screwed up"!!! Up to now, I haven't found a way to fix this problem. - Is there any workaround?
Regards, G.Graf

---

### Post by jocke on 2005-11-28
Yes! There is! :) There are instructions at Brother's site, but only when installing the CUPS wrapper, not at the LPR driver download page...

This is what you should have done before installing:

ln -s /etc/init.d/cupsys /etc/init.d/lpd

You could try to either remove or reinstall the package after writing the above. If it still doesn't work you can find more instructions [here]("http://lists.debian.org/debian-user/2005/04/msg01317.html") Hope this helps you.

---

### Post by geograf on 2005-11-29
[QUOTE=jocke]Yes! There is! :) There are instructions at Brother's site, but only when installing the CUPS wrapper, not at the LPR driver download page...

This is what you should have done before installing:

ln -s /etc/init.d/cupsys /etc/init.d/lpd

You could try to either remove or reinstall the package after writing the above. If it still doesn't work you can find more instructions [here]("http://lists.debian.org/debian-user/2005/04/msg01317.html") Hope this helps you.[/QUOTE]


YES! This is the clean solution! :D  - but a LPD Spool-Directory is also needed:

mkdir /var/spool/lpd

..fixed the problem completely!

THX for this Tip,
Georg

---

