---
title: "HPLIP - Ghah!"
date: 2009-10-21
forum: Hardware
---

### Post by ciaopaulo on 2009-10-21
Hi all,

I've got an old HP Deskjet (895Cxi) I'm trying to get working again.

I want to run the head cleaning functionality but I see that this option is greyed out, and I only have a print test page option.

Then I do a bit of googling and figure out that HP provide a bit of software which includes this functionality, plus more.

I download and install from HP site. Run script.

Test page from HPLIP seems to work, but any regular print gets spat out with "**** Unable to open the initial device" written across the top of the paper. The print stops without feeding out the paper and I have to force it to feed out the paper using the paper jam button!

So I uninstall, and try to reinstall via the Applications Add/Remove option. (Probably would have been the better way, but I forgot to check there first)

Stll doesn't work!

Uninstall that. Try to get back to regular printing (which I guess is still HP drivers anyway)

Printing is still cocked up. I have to reinstall all HPLIP pachages through synaptic.

*Sigh*

But even after uninstalling the HPLIP GUI ("Toolbox") I notice that it's still listed under System>Preferences. !!!

Can I get HPLIP to work, if not can I remove the poop from system preferences?

(Ubuntu 9.04)

---

### Post by Dark_Stang on 2009-10-21
At this point I would just download the latest hplip from here...
[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
Then install that. That way you know you have the latest and greatest software and it's intact.

Also, there isn't a button or button combo to press on the printer to clean heads? Even my ancient canon bubble jet 100 that printed at 1/2 ppm had that feature.

---

### Post by ciaopaulo on 2009-11-05
> **Dark_Stang said:**
> At this point I would just download the latest hplip from here...
[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
Then install that. That way you know you have the latest and greatest software and it's intact.

Hmm that's what landed me in the poop in the first place! It just didn't work!

> **Dark_Stang said:**
> 
Also, there isn't a button or button combo to press on the printer to clean heads? Even my ancient canon bubble jet 100 that printed at 1/2 ppm had that feature.

No not on this model, it seems to be a software driven thing. When you run the clean heads function it runs through a routine (who knows what) and prints off a test page. If the results aren't good you can run deep clean 2, and then finally deep clean 3.

Anyway, the problem was fixed,  the only way I managed to fix it was to to uninstall all HPLIP packages from Synaptic Package Manager (Complete Removal) and the reinstall.

---

