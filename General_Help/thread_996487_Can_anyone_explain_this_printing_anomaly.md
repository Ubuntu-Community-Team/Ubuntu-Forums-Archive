---
title: "Can anyone explain this printing anomaly?"
date: 2008-11-28
forum: General Help
---

### Post by mdurham on 2008-11-28
If you take a look at the image, the top half is from my monitor screen (oo word processor) the lower image is what would have been printed on my printer.
What could cause the missing characters when using the DejaVu Sans font?
Why is it okay in the word processor but not on the printer?
Cheers, Mike

---

### Post by rbmorse on 2008-11-28
I don't have any solution, but I can tell you that I have seen similar behavior with Latin characters on my HP 2605DN printer managed by HPLIP. 

I've only seen it manifest when using "text mode" applications like Gedit (and unfortunately printing checks from GnuCash where the number "8" prints as a box).  I've opened bug #277404 in Launchpad  on this, but I'm not sure if we're seeing different manifestations of the same problem, or separate problems with the same visible symptoms.

Oh...if your printer is Postscript capable you can install a new instance and use the generic .ppd file at /usr/share/ppds/cups-included/postscript.ppd  That one works for me.

---

### Post by mdurham on 2008-11-28
Thanks for the reply rbmorse, so I'm not alone. I too have an HP printer, it's a laserjet 1020 so there is at least a common element between us. I don't think my printer is Postscript capable, but the faulty part of the image that I posted was actually printed to a .ps file. I found I didn't need to actually print stuff on the printer to see if was okay, I just send it to a .ps file first.
It's not a big deal as we have other Chinese fonts that we (I mean, my wife) can use, I was just curios.
Thanks again, Mike

---

