---
title: "Slow firefox scrolling with nvidia drivers FIX"
date: 2009-01-06
forum: Hardware
---

### Post by punkrockguy318 on 2009-01-06
Ever since I installed Ubuntu 8.04 on my brand new Dell XPP M1530 laptop, I've been plagued with slow scrolling in firefox, most noticeably with sites with a lot of pictures (facebook, myspace, even slashdot).  When scrolling, it would cause CPU usage to jump to 100% and if I was playing any audio it would skip.  This was a very annoying problem.  However, to fix this issue, I simply added these lines to my xorg.conf under the "Device" section:

```

	Option  "GlyphCache"	"1"
	Option  "InitialPixmapPlacement"	"2"

```

this makes the bottom of my xorg.conf look this this:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option  "GlyphCache"	"1"
	Option  "InitialPixmapPlacement"	"2"
	Option	"NoLogo"	"True"
EndSection

```

I had brought this question up frequently in IRC but with no answers, but this finally fixed my problem.  I hope others will find this useful.

---

### Post by jgneff on 2009-05-02
Wow, that worked great! Thank you!

For reference (and future Google searches), I was getting extremely slow scrolling with Firefox after enabling the "Normal" or "Extra" Visual Effects (Compiz) in the Appearance System Preferences for Ubuntu 9.04 Desktop (Jaunty Jackalope). I have an NVIDIA Quadro FX 550 with NVIDIA Driver Version 180.44, and I'm using Mozilla Firefox 3.0.10 with "Use smooth scrolling" enabled in my Firefox Preferences under the Advanced, General, Browsing section.

Without the extra desktop effects, the scrolling was fine, but as soon as I enabled the effects, scrolling in Firefox became unbearably slow. These two settings in my "/etc/X11/xorg.conf" file completely fixed it.

Now, if only I can find documentation on exactly what GlyphCache and InitialPixmapPlacement really do ...

Thanks again!

John Neffenger

---

### Post by rainwalker on 2009-08-08
YES! THANK YOU!
Wow, you have no idea how awesome this is. I too have an Nvidia Quadro, and scrolling in Firefox was painfully slow using the proprietary driver (I installed the 185.18.14 one myself), but this fixed it completely!

---

### Post by rainwalker on 2009-08-09
Ah, I lied. That worked yesterday when I did it and restarted X, but things are slow again :?

---

