---
title: "Suspend working in Averatec 3715 (unichrome video)"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by Watonga on 2006-07-29
After much trial and error, I've got suspend working in my Averatec 3715-EH1.

I discovered thst suspend worked if I changed my video driver on xorg.conf from "via" to "vesa." So, in /etc/default/acip-support, I added all the modules I could think of that have to do with video to the blacklist, so that they are unloaded and reloaded when the computer resumes.

So, to get suspend working for me, in /etc/default/acip-support I changed this:

MODULES=" "

to this:

MODULES="via dri glx glcore"

---

