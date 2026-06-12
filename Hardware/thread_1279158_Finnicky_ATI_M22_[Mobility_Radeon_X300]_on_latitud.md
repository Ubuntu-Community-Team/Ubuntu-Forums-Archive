---
title: "Finnicky ATI M22 [Mobility Radeon X300] on latitude d610"
date: 2009-09-30
forum: Hardware
---

### Post by lazerblade on 2009-09-30
I just got a new dell latitude d610.
Ubuntu supported my WI-FI and sound card out of the box. :D

But, every time I run an application that uses 3D acceleration,
my computer crashes. The crashes vary. The 3D desktop effects
work though.

I think the drivers may be goofed up.

I googled around for a day, and didn't find anything that worked.

Does anyone know anything about this?
Anyone experiencing a similar problem?
Anyone know how I might be able to fix it?

Any help would be appreciated.

Thanks!

---

### Post by lazerblade on 2009-10-30
Bump! :???:
Somebody has gotta have something.

I found one solution here:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

But as soon as I upgraded to Karmic Koala (9.10), my video drivers
went loony again, and now I can't even start gdm. My system won't
boot except from a recovery prompt. And then when I try to start
gdm, it tells me there are no screens to start it on.

I would greatly appreciate any advice/help/solutions anyone may have.

---

### Post by famaster on 2009-10-31
I had the same problem... when I followed the instructions for Karmic, gdm uninstalled somewhere in there.  I can't reinstall gdm with the Intrepid source list b/c it says its obsolete, but when I install it with Karmic, it installs a lot of xorg components that make it useless.

I reinstalled gdm from the command prompt anyway when I rebooted, then when I got in all the icons were the old ones and Hardware Drivers doesn't seem to find anything.  I did manage to install the proprietary drivers from AMD's page, but other than the ATI Catalyst application, it did nothing.

I guess it's just old hardware now, for me anyway, even though I'm sure older hardware is supported, but not from ATI.  The open source drivers aren't the best, but maybe they'll get better sometime, so I'm going to mess with that after reinstalling.  If anyone has found a way to get the proprietary software to install, I'd like to know it too. :)

btw, I'm not sure how much longer Intrepid is going to be supported.  Is it a good idea to save the packages?

---

