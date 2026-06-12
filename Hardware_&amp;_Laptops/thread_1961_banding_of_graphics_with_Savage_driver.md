---
title: "banding of graphics with Savage driver"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by UberGeek on 2004-10-24
Has anyone experienced this ?
If I use the savage driver (the driver for my ThinkPad T22) I get very bad banding of gradients in X.
However if I use the vesa driver the problem is not there.
I have set the default color depth to 24 bits with the savage driver but it does not seem to help.
I could keep using the vesa driver, but would prefer to use the native driver if possible.
Any suggestions would be welcome.

Other than that I have, so far, had no problems with Warty.

---

### Post by mduduzi on 2004-10-27
[QUOTE=UberGeek]Has anyone experienced this ?
If I use the savage driver (the driver for my ThinkPad T22) I get very bad banding of gradients in X.
However if I use the vesa driver the problem is not there.
I have set the default color depth to 24 bits with the savage driver but it does not seem to help.
I could keep using the vesa driver, but would prefer to use the native driver if possible.
Any suggestions would be welcome.

Other than that I have, so far, had no problems with Warty.[/QUOTE]

I can't say my graphics banding is that bad, but is sure doesn't look like 24-bit to me. I have the onboard Savage Pro (with VIA KN266 chipset). What configuration utility did you use to change your colour depth?
II'm new to Gnome --it took no less a distro than Ubuntu to get me of KDE. So I'm fairly lost when it comes to hardware configuration utilites in both GNOME and Debian.

---

### Post by oscarh on 2004-11-18
run in 16 bits, that will fix the banding.

don't really know why this happends.
check out savage wiki, [http://www.probo.com/timr/wiki/moin.cgi/FrontPage](http://www.probo.com/timr/wiki/moin.cgi/FrontPage), for more info on savage cards.

---

