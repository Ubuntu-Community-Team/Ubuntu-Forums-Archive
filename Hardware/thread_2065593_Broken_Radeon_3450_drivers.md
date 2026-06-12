---
title: "Broken Radeon 3450 drivers?"
date: 2012-10-02
forum: Hardware
---

### Post by gnome_nz on 2012-10-02
Earlier tonight I had Compiz etc running happily on a ATI Radeon 3450 card.   Then I tried to get things working with a second monitor which I sometimes use. Didn't like the result (esp as it killed Compiz) so went back.     

Now I can't get the "Extra" visual effects enabled again.  Further, a glance at Xorg.log.0 says that the driver is reporting the card as an "unknown 3rd party" card, whereas an earlier log shows it detected quite alright.     

I've tried reinstalling all the ATI related packages I can find, and I've deactivated and reactivated the ATI Fire GL driver. Still no luck.     Have also checked the card's temp etc. Not overly hot, and is seated OK now.    

Running Ubuntu 10.04

Would appreciate any suggestions.     

Thanks.

---

### Post by gnome_nz on 2012-10-03
Got it fixed.. In the end I had to visit the AMD site and download a full driver from them (not sure if I did this first time round but the installer looked familiar) and ran that, after clearing out all the Radeon related files via Synaptic (and a couple I must have missed - the AMD installer told me what to remove). 

She's back.. Now, to figure out how to get this other screen working properly.. Without breaking things again!

---

