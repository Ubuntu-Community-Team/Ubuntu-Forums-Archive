---
title: "asus xonar u1 (usb) in kde"
date: 2008-10-21
forum: Hardware
---

### Post by wonko on 2008-10-21
I've just tested my newly bought asus xonar u1 usb audio station, and I can't get it to work. I've tested it on two pcs running kubuntu 8.04 and one running kubuntu 8.10 beta. All gives the same result; when I plug it in, the led turns purple (or pink), and when I restart kmix I can choose "USB Advanced Audio Device", but this only shows the "input" and "switches" tabs, no "output" tab. And all sound comes from the onboard card (I've tried switching this off too, yielding no sound at all).

There is one strange exception, though; when loggin out from kubuntu 8.10 (kde4), the logoff sound is played over the xonar, while the led flashes blue/ purple. In kde4 I can also find the xonar under system settings -> sound, where I can prioritize the xonar over the onboard card, without it making any difference.

I've read [on this forum]("http://ubuntuforums.org/showthread.php?t=799163"), that it should work in ubuntu 8.04 (under gnome, i guess), and I'm wondering if anyone has any idea why it shouldn't work under kde (I'll try it under gnome soon, and post back if it's successful).

Update: found a partial solution; installed asoundconf-gtk, as suggested [here]("http://ubuntuforums.org/showthread.php?t=954325"), and now amarok (at least) plays over the xonar. It didn't change the kmix though - it still only shows input and switches tabs. But, for some reason, I can adjust the volume using the "pcm" lever on the "input" tab..

---

