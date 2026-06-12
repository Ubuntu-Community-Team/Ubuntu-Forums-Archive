---
title: "HP Restrictive Practices (G5056EA laptop)"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by arst06d on 2008-02-28
Hi

I have recently acquired a nearly new HP laptop, model G5056EA.  This came bundled with Vista which was quickly removed and raplaced with Ubuntu 7.10.  Installed easily and the only fiddling I had to do was to get the restricted driver working for the Broadcom wireless card - thanks to posts on this forum for help.

A couple of minor irritations however:

During boot up of Ubuntu I get several messages along the lines of > cannot allocate resource region 7 of bridge .... blah.  This causes no problems that I can see and other posters have said it's nothing to worry about - maybe fixed in Hardy, but maybe just needs a BIOS update.

And here's the rub:

HP support site has updated BIOS available, but only as Windows Installers.  I wrote to support and received the following reply (quick response, though, to be fair):> As the HP G5056EA Notebook PC is bundled with Windows Vista, we do not have BIOS versions for non Windows based BIOS update for the Notebook model.

The only option to install the BIOS update is from Windows operating systems.


Now surely this is a restrictive practice, locking in a user to a specific operating system?  I'll be writing to the Office of Fair Trading for all the good it will do.

I used BertPE to burn an XP LiveCD, but it didn't have support for my USB stick where the update is.

Can I extract the appropriate update from the installer somehow and update manually?  Any ideas welcome.

Oh, and another thing I'll be whinging about - I wanted to change the Broadcom mini PCIe card and bought a Gigabyte GN-WL01GT and the cheeky sods have a restriction on the type of wireless card you can install.  Again, maybe loosened in a later BIOS version and we go round in a circle again.

I've seen posts where people have either hacked the card itself to change its' identity, or hacked the BIOS whitelist to add get the card recognised, but I really don't have the expertise or inclination to go down that route.

Commenst & suggestions welcome.

---

### Post by MiataMuc on 2008-02-28
Hi,

I think there is no other way to use your new WLAN-card except manipulating either the bios of your computer or the card itself; the latter option does not sound as risky as the first..
As far as I know, the reason for this blacklisting is caused by the fact, that the manufacturers of the laptops have to guarantee rf-parameters to get FCC-approved; they do this by tuning the rf-parameters of the card to the antenna of the respective laptop-model.

May one should get HP to offer their Bios-updates the same way as Lenovo does: as an indows-binary and as an bootable CD-Iso (afaik Freedos based).
But one question concerning the Bart PE-System: can't you just slipstream the required files to the image?


Flo

---

### Post by arst06d on 2008-02-28
> slipstream the required files to the image
sorry - no idea how to go about this.  I'll do some digging

---

### Post by arst06d on 2008-02-28
OK, we have progress.

I had another look at Bart's PE Builder and it has the option to include additional files in the .iso it creates, so I added the BIOS update utility files, burned the iso to cd and booted up.

Had to copy the utility files to the RAMdisk part of the system as the utility needs write access.  Ran the BIOS update and all is OK.  

Booted back into Gutsy.  Still getting the "cannot allocate resource.." messages on startup, but I can live with that.

Now to install the new card and see if the restriction has been lifted - not holding my breath, mind.

Thanks for your help.

---

### Post by arst06d on 2008-02-28
As we thought - the card is still not recognised and the laptop will not boot up with it installed.

Any Janet & John instructions on changing the card internals to spoof the BIOS?

---

### Post by MiataMuc on 2008-02-28
Hi,

sorry, I only know about the bios / card . manipulating methods - I had a similar problem some months ago, and decided not to change my card in the end. 

Flo

---

