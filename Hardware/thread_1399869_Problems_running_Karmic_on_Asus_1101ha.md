---
title: "Problems running Karmic on Asus 1101ha"
date: 2010-02-06
forum: Hardware
---

### Post by sharathcshekhar on 2010-02-06
Hello everyone,
I bought a Asus 1101ha Netbook recently and installed Karmic into it. After following the howtos to install the GMA500 drivers, I managed to get my netbook running on Ubuntu 9.10 the pretty decently.

But the major problem which is making me impossible to use Ubuntu is, frequently my display freezes and only colored horizontal lines keep flickering and nothing works, even the keyboard stops responding. Rebooting is the only option :-( 

I observe that my fan runs at a very high speed when running Linux and Temperature of processor goes too high(60 deg. Cel).. I was wondering if this is the reason for the display to freeze?

Anybody successfully running Karmic on 1101HA?
Any help will be appreciated. Thanks in advance..

Regards,
sharath

---

### Post by lidex on 2010-02-06
[***_[SIZE="4"]http://www.google.com/search?q=Asus+1101ha&sitesearch=ubuntuforums.org[/SIZE]_***]("http://www.google.com/search?q=Asus+1101ha&sitesearch=ubuntuforums.org")

---

### Post by PvSinNL on 2010-02-07
> **sharathcshekhar said:**
> But the major problem which is making me impossible to use Ubuntu is, frequently my display freezes and only colored horizontal lines keep flickering and nothing works, even the keyboard stops responding. Rebooting is the only option :-( 

I observe that my fan runs at a very high speed when running Linux and Temperature of processor goes too high(60 deg. Cel).. I was wondering if this is the reason for the display to freeze?

Anybody successfully running Karmic on 1101HA?
Any help will be appreciated. Thanks in advance..

Unfortunately, I don't have a clue as to what could be causing your problem, but I can report that I've got Karmic running on a 1101HA without these issues.

It sounds like you've got some rogue process eating up all CPU cycles. Did you check System Monitor, top, or powertop to figure out what could be the culprit?

---

### Post by lidex on 2010-02-07
If you're using the poulsbo 3d driver you can uninstall it or look here for a fix:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290")

---

