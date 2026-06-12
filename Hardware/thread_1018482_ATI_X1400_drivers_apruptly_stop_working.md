---
title: "ATI X1400 drivers apruptly stop working"
date: 2008-12-22
forum: Hardware
---

### Post by konradpiskorz on 2008-12-22
Hello,

I have a toshiba tecra A6 laptop with an ATI mobility radeon x1400 which I have been running ubuntu very happily since may of this year.  Scroll to -X-X-X-X if you're not interested in my story :(



I have been using the ATI proprietary drivers downloaded from ati's website.  These have worked since may and still worked with an upgrade to Hardy Heron.

Now after doing something(which I don't remember what), well the drivers stopped loading and Ubuntu would only load to low graphics mode.  Ok I had the ati file on my desktop as reinstalling the driver had become a standard procedure in learning to use ubuntu and linux.

Now I was in a big rush and had a class to get to, so i shoved the laptop in my bag and just forgot about it.  Well anyways pulling it out an hour and a half later, i found out it did not display things properly.  It was still working, just with big fat ugly purple lines all over the place.

So the warranty replaced the video card and i had my computer back, ready to reinstall the ati driver and be on my merry way... or so i hoped.


-X-X-X-X-X-X-X-X-X-X-X-X


So I reinstalled the ati proprietary drivers(from ati's website) as I had always done when I messed something up graphically.

Except this time it just didn't work.  And nothing I could do could get my drivers to work...  It kept tossing back to the default mesa3d drivers.

Now I have spent a good portion of my time trying to get these drivers to load, which had no problem loading before.  Now what I found was that everyone with the same problem seemed to have it upon upgrading to hardy heron, which I had done many months previously.

So it seems that at some point this occurs
dmesg reports in one line
```
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
```

ok... whatever that means... 

So I tried a variety of options.  I removed my xorg.conf completely, I reconfigured it with aticonfig, with dpkg-reconfigure xserver-xorg.  By manually deleting it and making a new file absolutely removing any indication of ati or fglrx from my system and THEN reinstalling the drivers. And then doing the first steps again to see if it would do anything.

I did this for three different versions of the drivers, two of which I had used before with no problems.  I tried the driver in ubuntu's repository which didn't work either.

ok so finally I found on fellow who said

> I found the problem: When I had compiled the kernel I hadn't set /usr/src/linux to point to the correct directory. I created a link from /usr/src/linux->/usr/src/linux-2.6.7, recompiled and installed the new kernel, emerged the ati-drivers, and VOILA, all was well again.

on another forum (gentoo).

Well ok, I don't know anything about recompiling kernels and I don't see why I would need to given that the drivers were working PERFECTLY fine before on this particular kernel.

So I restarted and loaded kernel 2.6.24-19-generic instead of 2.6.24-21-generic which came with the ubuntu installation.

Now I loaded up in normal graphics mode, 1200x800 as it should be and got excited thinking this could be a workaround.

However I quickly looked and saw that restricted hardware settings told me that there were no proprietary drivers AT ALL and loading up ati catalyst control center (which has been barking at me that ati drivers werent loaded and hence it cant start) loads up perfectly!  I was excited, the only problem it turned out was my kernel...

And then I saw that the drivers loaded were still MESA3D!!!

What?!?!

So no matter how I install the drivers they don't load.  Even trying to do it manually.
No matter what I do to my xserver, it will not take the drivers.

kernel 2.6.24-19 runs at 1200x800 mesa3d drivers and loads ati control centre and shows NO restricted drivers available
kernel 2.6.24-21 runs at 800x600 mesa3d drivers and doesn't load ati control centre and does show ati restricted drivers

Anyways I'm at wits end... Any help on this guys?

---

### Post by konradpiskorz on 2008-12-22
Well after two days of struggling with my computer to no avail, I turned it on today to find that the 2.6.24-19 kernel NO LONGER LOADS!

However the 2.6.24.21 kernel once again works perfectly and the drivers are loading again... And I did nothing but wait one night and now it works...

WTF

---

