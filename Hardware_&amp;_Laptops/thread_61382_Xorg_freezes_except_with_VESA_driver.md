---
title: "Xorg freezes except with VESA driver"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by haakon on 2005-08-31
Hi,

I have an ATI Radeon 9200 (inexpensive and good enough for my needs). It has always worked fine, but after I installed Ubuntu (granted, on a new mobo/CPU/RAM), it has been acting up.

The Ubuntu install set up xorg.conf to use the driver "ati". After a while, Xorg freezes. Some graphical artifact will appear on the screen, and I can still move my mouse around, but I cannot press any buttons or anything, and the keyboard is unresponsive (for instance, pressing Caps Lock doesn't trigger the Caps Lock led). So I have to press the reset button to reboot, but now, as soon as GDM appears after the reboot, the whole screen is covered in some sort of badly colored stripes, and everything is frozen again. I have to boot in recovery mode to edit xorg.conf.

Since I remember having used the driver "radeon" before, I substituted "ati" for "radeon", but the results were the same (horrible stripes after reboot). If I use "vesa", it works. But of course, VESA is slow and I cannot even play movies in Mplayer.

I can sometimes turn the system off for a while and then on again, and the stripes will be gone and things will work. However, after a while (one hour, 2 days, who knows), it will freeze.

I have tried to do various things in BIOS, like changing the AGP aperture size, but nothing seems to work. So I'm wondering if there are any suggestions around? (I'm afraid using the proprietary ATI drivers is not an alternative for me)

Thanks,
Haakon.

---

### Post by ry_ry on 2005-09-01
You might want to try this:

Driver         "ati"
Option         "NoAccel"               "true"

in your Device section.

---

### Post by haakon on 2005-09-01
[QUOTE=ry_ry]You might want to try this:

Driver         "ati"
Option         "NoAccel"               "true"

in your Device section.[/QUOTE]

Thanks a lot for the reply, I'll try this as soon as I get home. Hope it works, I hate this :)

Edit: Just an addition bit of info: there are no errors or warnings in the xorg log after a freeze.

---

### Post by haakon on 2005-09-01
I suppose adding Option "NoAccel" "true" will disable hardware accelleration (DRI)? What I tried now after googling some in addition, was to comment out the 'Load "DRI"' line. It hasn't frozen so far, so it seems promising. However, I now of course have no DRI. If there is any solution that allows me to keep DRI, I would of course prefer that, but I'm no gamer so it isn't critical.

---

### Post by ry_ry on 2005-09-01
[QUOTE=haakon] (I'm afraid using the proprietary ATI drivers is not an alternative for me)

Thanks,
Haakon.[/QUOTE]

If you change your mind about using the proprietary ATI drivers then have a look at this "How to:" on installing them. This worked on my system, and you can go to ATI website and download the ATI installer for your Radeon 9200 series card. I believe the driver version is 8.16.20 now, so just insert into the "How to:" the new version number and you should be set to go.

Here is the link to the "How to:" that worked for me.
Scroll down to Epskampie posted "How to:" and try that.
[http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10&highlight=ati+fglrx+8.14.13](http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10&highlight=ati+fglrx+8.14.13)

Hope this helps.  :)

---

