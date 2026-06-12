---
title: "Restricted drivers manager not seeing my ATI card?"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by madscientist on 2007-07-05
When I run System -> Administration -> Restricted Drivers Manager, it says "Your hardware does not need any restricted drivers." and then closes.

But, I'm pretty sure that's not true.  lspci says, for example:

   01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

Can anyone tell me what might be causing the RDM to not recognize my video card?

I do have xorg-driver-fglrx installed and my xorg.conf uses fglrx, and I have linux-restricted-modules installed.  These are there from previous releases of Ubuntu (6.06/6.10) before the RDM was available.  Is this causing the problem?  Anyone have any ideas about how to "back out" those things and let RDM take over?

---

