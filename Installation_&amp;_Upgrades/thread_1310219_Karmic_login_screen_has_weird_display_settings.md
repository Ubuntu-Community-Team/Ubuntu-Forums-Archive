---
title: "Karmic login screen has weird display settings"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by enque on 2009-11-01
I have searched the forums extensively and found no other who have asked this.

_The question:_
How do I change the screen resolution and color depth settings for the login screen? (in Karmic Koala)

_The background info:_
I just upgraded to Karmic Koala. The new login screen is set to a weird resolution which stretches OUTSIDE the edges of my display; when I move the cursor towards the edge of the screen the image pans that way so I can see more.

This also causes the bottom menu-bar (with the logon settings and such) to be placed incorrectly (hovering closer to the middle of the screen). Also, the color depth is set very low which makes the background look ridiculous.

A few seconds after entering my password the screen is finally set to my normal (good) settings. My normal settings (nvidia-settings) are 1680*1050@24bit.

---

### Post by nelsonrp on 2010-01-02
Hi,

I had the same problem on a Dell XPS M1530. The login screen was 2400x900 px and after logging in it was set to a normal with (1440 in my case). I corrected it editing xorg.conf (/etc/X11/xorg.conf) replacing **Virtual 2464 900** for **Virtual 1440 900**:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual 1440 900
#		Virtual	2464 900
	EndSubSection
EndSection

```

Hope it helps.

---

