---
title: "Dell Inspiron 17 i5 Resolution problem!"
date: 2010-02-07
forum: Hardware
---

### Post by darkerlink on 2010-02-07
I just purchase this beat of a laptop. It's a dell inspiron 17 with the i5 intel quad core processor. My problem is the resolution is sooo low. I can't get it higher that 1024x768. Even with this setting it looks like it's 800x600 on this big 17 inch screen. The windows 7 version was supporting a 1600 display. I've checked System>Admin>Hardware Drivers but there was nothing there. Can anyone help? This is brand new purchased from Best Buy.

installed is a fresh version of 9.10 64 bit.

---

### Post by darkerlink on 2010-02-08
okay i fixed the problem with 

sudo gedit /etc/X11/xorg.conf

and changed "vesa" to "intel" but there are still problems.Video playback is really choppy. The computer freezes while trying to enable the medium setting in compiz and I cant even run glxgears. It will freeze. Can anyone help? I've found tons of thread on intel GMA but this is the gma HD only found on i3 and i5 intel processors.

---

