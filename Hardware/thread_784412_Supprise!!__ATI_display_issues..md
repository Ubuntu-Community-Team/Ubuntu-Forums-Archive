---
title: "Supprise!!  ATI display issues."
date: 2008-05-06
forum: Hardware
---

### Post by cstudler on 2008-05-06
Here is what I have.  My laptop is a Gateway MX6441.  It has an AMD Turion ML-34 1.8 GHz processor, 1.4 GB RAM, ATI Radeon Xpress 200M with 128 MB.  I am running Ubuntu 8.04 LTS.  I've installed the ATI restricted drivers, and when a screensaver runs or when I view a video in a window, the screen will flash every few seconds.  When I view a video fullscreen, the flashing seems to stop.  Also, I notice the flashing mainly when using the gxine video player.  I see it when using other players, such as Totem, but less so.

---

### Post by cubeist on 2008-05-06
> **cstudler said:**
> Here is what I have.  My laptop is a Gateway MX6441.  It has an AMD Turion ML-34 1.8 GHz processor, 1.4 GB RAM, ATI Radeon Xpress 200M with 128 MB.  I am running Ubuntu 8.04 LTS.  I've installed the ATI restricted drivers, and when a screensaver runs or when I view a video in a window, the screen will flash every few seconds.  When I view a video fullscreen, the flashing seems to stop.  Also, I notice the flashing mainly when using the gxine video player.  I see it when using other players, such as Totem, but less so.

Yes, this happens to me too on an ati hd3200 embedded chip.  I saw one post where there was advice to add the option "TexturedVideo" "off" in the xorg.conf file but this did not work for me.  Interestingly I don't have the problem with vlc, and I don't use a screensaver.  However, when I load up flightgear it flickers, or flashes, horribly.  Thus the easy fix is just to drop out of compiz (did I mention this only occurs with compiz on) by using alt+f2 and then metacity --replace.  compiz --replace brings it back when I am done.

---

