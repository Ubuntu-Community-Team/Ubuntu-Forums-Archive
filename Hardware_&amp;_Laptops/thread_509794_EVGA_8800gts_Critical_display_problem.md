---
title: "EVGA 8800gts Critical display problem"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by davem2312 on 2007-07-25
Hello all,

I recently purchased a new EVGA 8800gts 320-mb version.  So here's the deal.  The card works fine in Windows, and seems to run really well.  However, when I began to start up Ubuntu, grub loaded fine, and... I get a completely black screen... OK, well this must be an xorg.conf problem right?

Wrong.  Edited Xorg.conf many times from (recovery) mode, installed nvidia beta drivers from scratch...etc ran sudo dpkg-reconfigure xserver-xorg... recognizes my 8800gts, and Dell 2407 WFP... etc.

Next thing... maybe a fresh install of ubuntu will help.  I pop in the disk, and still, no display.  OK, how about "Safe graphics mode" off the live cd will help... still.... nothing past the original menu.

These black screens are not dead, it is simply putting a black screen out there, since the monitor does not go into "sleep" mode.  Here is my general setup.

AMD Athlon 64 X2 6000+
Biostar TFORCE TF7025-M2
2GB DDR2 800
EVGA 8800gts 320mb edition

Can anyone help, or is it simply.... "I must have bad hardware"?

Thanks,
Dave

---

### Post by davem2312 on 2007-07-25
Well, I have somewhat more information.  I found a few other people with similar problems.

When I turn off the "splash" setting in the boot script, the loading is fine.

Any speculation??

---

### Post by animeboi252 on 2007-07-25
nice system anyway have you tried to install ubuntu again maybe:confused:

---

