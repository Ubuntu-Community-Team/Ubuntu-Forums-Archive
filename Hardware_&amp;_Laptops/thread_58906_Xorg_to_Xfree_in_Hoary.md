---
title: "Xorg to Xfree in Hoary?"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by landotter on 2005-08-22
Easy enough to switch packages using apt-get, problem is configuration. I get an X error upon boot.

I'm assuming that's because I don't have a proper /etc/XF86Config-4 file in place.

Now where to get one of those? Rename the xorg.conf file? :P

Reason I'm switching is that Xfree works great with my onboard i810, but with Xorg, I get no acceleration. Thus no OpenGL flying toasters and other delights.

There are patches for the i810 floating about, but it seems easier to just "downgrade" as it all worked fine in Warty.

Thanks!

-Max

Edit: I resaved the xorg.conf file as the XF86Config-4 file thinking--why not? LOL

Booted just fine. No acceleration still. :/
Added "Videoram=xxxx", restarted X and no go.

any takers or do I need to hook up my failed Warty drive and see if I can extract the config file? (doubt I can even mount it)

---

### Post by landotter on 2005-08-22
AHA! It's a colour depth issue.

Edited the config file to 16 instead of 24 and restarted X--done. :)

---

