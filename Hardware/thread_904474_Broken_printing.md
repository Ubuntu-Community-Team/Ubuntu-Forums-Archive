---
title: "Broken printing"
date: 2008-08-29
forum: Hardware
---

### Post by hambone79 on 2008-08-29
I have an HP Photosmart 7450 printer that was working fine with CUPS on Fedora 8 but every since I switched to Kubuntu 8.04 it has been acting up on me. Here is what happens...

1. I start a print job. If the print has been sitting for a while (few hours/days) the printer won't do anything. If I check the HP Printer Toolbox or the CUPS administration page, it says that it can not communicate with the printer.
2. When the above error appears, I clear the print queue and then turn the printer off and back on.
3. I start the print job and everything works fine, but if I start a second print job the whole process starts all over.


I have moved the printer to my work laptop (running XP) and it doesn't have any problems using the printer. Also, since I didn't have any problems on Fedora, I believe there is something wrong with the Kubuntu HP drivers and/or CUPS.

Does anyone know how to fix this problem? It's extremely irritating!

---

### Post by phidia on 2008-08-29
There is a somewhat related report [here]("https://answers.launchpad.net/hplip/+question/43114"), and I think the advice there applies to you too.

> Try deleting the printer queue and running hp-setup to configure the device again. If it still doesn't print print run hp-check again and make sure the plug-in is installed. If it's not run hp-plugin and it should install the plugin.



---

### Post by phidia on 2008-08-29
Sorry I don't know why this double posted. But the forums do lag terribly sometimes-still I only clicked once!

There is a somewhat related report [here]("https://answers.launchpad.net/hplip/+question/43114"), and I think the advice there applies to you too.

> Try deleting the printer queue and running hp-setup to configure the device again. If it still doesn't print print run hp-check again and make sure the plug-in is installed. If it's not run hp-plugin and it should install the plugin.



---

### Post by hambone79 on 2008-09-18
I tried what you said, but it is still broken. After looking around for a bug report I came across Bug #241781 ([https://bugs.launchpad.net/ubuntu/+bug/241781](https://bugs.launchpad.net/ubuntu/+bug/241781)) which describes exactly what my printer is doing. It appears that this is a confirmed bug.

---

