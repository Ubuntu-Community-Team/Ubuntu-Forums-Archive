---
title: "No PCMCIA"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by encompass on 2006-06-04
I have installed the new xubuntu, very excited about the dri support for my card now working.  But after an very smooth install I lost the support for my Wireless card.
Further investigation shows that my pcmcia card is either not detecting the card or not working at all.
The lappy had fully hardware support in Breezy except for the DRI drivers were not built in.
The wireless card is an orinoco silver, a VERY compatible card.
I have tried restarting pcmcia services but with no change.
Any ideas?
8)

---

### Post by encompass on 2006-06-04
Cool figured it out...
well, could have been two things
one, I cold rebooted the computer... seems to have made everything run a little smoother.
two, I installed pcmcia-cs it said while installing it that it was outdates and to be replaced by the one I was currently using.
But any, works now... as it seems...
Hope it helps someone else out there too...

---

