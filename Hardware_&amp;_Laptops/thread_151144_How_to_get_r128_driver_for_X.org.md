---
title: "How to get r128 driver for X.org"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by harisund on 2006-03-27
Hello

I have Dell Latitude C800, a laptop with ATI Rage Mobility M4 AGP 4x graphics card.

I understand the following:
(.) Rage Mobility cards are cards designed by ATI for laptops. Here is the official page ([http://www.ati.com/products/mobilitym4/index.html](http://www.ati.com/products/mobilitym4/index.html))
(.) Unfortunately it is listed in the ATI Discontinued products page too ([http://www.ati.com/products/discontinued.html](http://www.ati.com/products/discontinued.html)) Does that mean Ubuntu won't support it?
(.) From my laptop's documentation ([http://support.dell.com/support/edoc...pecs.htm#video](http://support.dell.com/support/edoc...pecs.htm#video))
it's default resolution is 1600 x 1200 (UXGA) at 60 Hz.
(.) When I install Ubuntu Breezy it defaults to that resolution. There was an online documentation of someone installing Debian , and that was at 1600x1200.
(.) Running it at this resolution is genuinely crazy. I can't see a thing. And it simply refuses to run at a lower resolution. At 1024x768 (what I want) it gives me a totally garbled screen.
(.) I am able to run 1024x768 using vesa. However, it doesn't have 3d accelration and in general is quite slow. glxinfo says no direct rendering, and glxgears gives me a totally rocking fps of about 50.

after searching these forums, I understand there is a driver called r128 that is supposed to be in support of this card (the ATI official page says this is based on Rage 128 cards.)

So, how do I install r128 driver? I do a dpkg-reconfigure xserver-xorg, I don't see the r128 driver listed. Under r, I only see a rendition driver !

Can I install r128 driver for Xorg that comes with Breezy? Also, how do I find out which version of Xorg I am running?

Also, once I install the r128 drivers, I will also most probably be needing to know how to install this thing called DRI? What's that about? I believe that is needed for r128 drivers?

My biggest worry of course is whether r128 can be installed, and whether Breezy can support my card. Do you think Warty might?

Thanks !!

---

### Post by evilgold on 2006-03-27
your best bet would be to go with the "ati" driver. Older ati cards are only supported by that (and the radeon driver). It comes with ubuntu so just switch "vesa" to "ati", no install needed.

also if the reolution problem keeps happening, post your xorg.conf and maybe i can provide more help.

---

### Post by Teroedni on 2006-03-27
You need to use driver  "r128"

For more info about this opensource driver
Type

```
man r128
```

in terminal



Hopes this helps:)

---

