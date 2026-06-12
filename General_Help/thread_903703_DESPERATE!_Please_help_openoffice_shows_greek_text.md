---
title: "DESPERATE! Please help: openoffice shows greek text fine, printer messes them........"
date: 2008-08-28
forum: General Help
---

### Post by the mage on 2008-08-28
Ok, the past few months I started spreading ubuntu to some friends and relatives...
Four days ago me and an uncle of mine (lawyer) went to a shop, so he could get a new pc, and there I suggested him trying ubuntu on a pc (he intended on buying a Mac again), so he followed my advice and got a pc. FRom then and every single day I have been trying to make that creep thing work!
Ubuntu has been sort of easy with me all of that time, but this time it is causing quite a problem.

He had some requests and well, after lots of efford I managed to take care of them, but there is still one problem...

He is a lawyer, and he writes in greek on Mac Word on his eMac, and has tons of text... His texts are not just in one font, they are quite complicate.
He needs to get the docs on his new pc, with the best conversion possible and stuff...
It took me two days to figure that thing, but after converting the mac fonts he needed and installing them on the PC/ubuntu I managed to have openoffice to display them almost as wanted (any help on making them even more like before would be nice, if possible...)

But then I try printing some pages (I tried a lot) and well, the result is dreadful...
some text exists, some doesn't some is totally messes, still greek but like...well weird. I tried then to install another driver for his HP laserjet 1022 but I either didn't do it right or it didn't work because even if the post here said it would be better , it got worst....

Please help :(
I just don't want to tdrop all that efford to the rubbish, put on his PC windows, and ubuntu losing not just one but quite a few ppl which he would recommend it...

---

### Post by simosx on 2008-08-29
Most probably this is an issue with OpenType fonts. The current version of OpenOffice.org has an issue when printing documents that reference OpenType fonts.

Could you please make a test by printing text, using the Sans (virtual for for DejaVu Sans) font? DejaVu is not an 
OpenType font, and has full Greek support.

OpenOffice.org 3.x appears to fix this issue.

---

### Post by simosx on 2008-08-29
You may also want to subscribe to this issue,

"support PS-OpenType/OTF/(SFNT with CFF) fonts for PDF export and printing"
[http://www.openoffice.org/issues/show_bug.cgi?id=43029](http://www.openoffice.org/issues/show_bug.cgi?id=43029)

---

### Post by Visual_Noiz on 2008-11-01
> **simosx said:**
> Most probably this is an issue with OpenType fonts. The current version of OpenOffice.org has an issue when printing documents that reference OpenType fonts.

Could you please make a test by printing text, using the Sans (virtual for for DejaVu Sans) font? DejaVu is not an 
OpenType font, and has full Greek support.

OpenOffice.org 3.x appears to fix this issue.

Thnx, I had the same problem and this helped a lot!

---

