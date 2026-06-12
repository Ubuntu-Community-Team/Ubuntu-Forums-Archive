---
title: "desktop effects could not be enabled"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by thick0 on 2007-12-16
I upgraded my hp nx 8220 from edgy to gutsy this morning. With edgy I had beryl working just nicely.

Since installing gutsy I can not get compiz fusion going. A few notes:

tim@martini:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

I went to the restricted drivers manager and enabled the ATI enabled graphics manager. I also modified xorg.conf to set "Composite" On.

But when I go to switch on normal visual effects, I get the message above. Any ideas?

---

