---
title: "Can't change screen resolution.  Standard fix not working"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by hysteresis62 on 2006-12-31
I just installed Ubuntu (V 6.06), and then downloaded and installed all updates from the Ubuntu mother ship (so to speak). Unfortunately, my screen resolution is set at 640x480, and there are no other options in the dropdown menu in System->Preferences.

I've checked around and tried the following fix people recommend.

I turned off gdm and ran dpkg-reconfigure. Ubuntu autodetects my video card (ATI 9100) seemingly fine. It can't autodetect my monitor (KDS XF-9bi), but I have the manual for it, and I entered in the horizontal and vertical refresh rates as specified there. I restarted gdm and no change. The xorg.conf file reflects the changes I made (the refresh rates are correct in there, and only the 1024x768 option is now in xorg.conf, which is the resolution I want), but the System->Preferences still only gives the 640x480 option, and that's still the resolution I'm getting.

At this point, I'm at a loss, and I just scrapped my old clunky redhat 9.0 for this, so I'd really like to be able to run Ubuntu. Help please! 

Thanks!
Joe

P.S. There's a lot I don't know about Linux, so don't be afraid to dumb down the language in advice--I won't be offended!

---

