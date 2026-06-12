---
title: "[SOLVED] meta keys (@) not working"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by liviubero on 2007-08-30
Hi,
I read the forums but couldn't find the answer I am looking for...
I have an AMILO M1437G with a German keyboard and I have installed Feisty on it.
The fact, after installing the fglrx driver and configuring the xserver (sudo dpkg-reconfigure xserver-xorg), now I get every time I log in an error window, telling "Error activating XKB configuration" (attached).

The German keys (Ü,Ö,Ä) are working, but the alt-key combinations are not.
I cannot write for instance "@" (that is alt+Q).

When I try to  change whatever in System->Preferences->Keyboard, I get only the same window I get at login (attached).

Is there any configuration I should change? 
I run  several times sudo dpkg-reconfigure xserver-xorg and chose every time "de "  for the keyboard.

Anyone having the same problem?

I'm just sick of this error window at login...

---

### Post by liviubero on 2007-08-30
?
Anyone?
Does anyone at least has installed Feisty on a Amilo M1437G?

---

### Post by liviubero on 2007-08-30
Could anyone with a Amilo M1437G and a German Keyboard post his /etc/X11/xorg.conf file in order for me to copy it? This would be, I think, the best method.
Thanks.

---

### Post by liviubero on 2007-08-30
All right, not knowing what to do, I just reinstalled Feisty (in German language this time) and then installed fglrx with Synaptic.
Then:
sudo dpkg-reconfigure xserver-xorg
selected the fglrx driver and let the default settings for the keyboard; if I didn't knew something, I just looked on the /etc/X11/xorg.conf file, to see how it already is, for instance for the mouse settings.
Now it is alright.
I can write @|\{}[]
Super!

---

