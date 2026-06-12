---
title: "compiz will not span monitors without glitches"
date: 2008-11-30
forum: General Help
---

### Post by unclben on 2008-11-30
Let me preface this by saying that Intrepid is the only distro with which I've been able to get dual monitors working anywhere near correctly. I've tried with all Ubuntus since Dapper as well as Fedora 8 and 9. As long as I use metacity, things run pretty well. The real problem, as the thread title indicates, is with Compiz.

edit: oops, forgot to mention I'm running Intel 965 integrated video.

Hopefully, the attached screenshot (which shows just what is on my right monitor - the left monitor is fine) will help describe the issue. When spanning 2 monitors with Compiz, the right half of the right monitor is all screwed up. The wallpaper in that area always has some kind of glitch - either it's missing altogether, or a second copy of the wallpaper image that overlaps the 'real' copy, or something else. In addition, any window that is open over that area has its image 'saved' there even after it's moved/closed/minimized (until another window is opened over that area).

Has anybody seen this before? My xorg.conf is included below. Note that the virtual desktop size (2880 x 1200) is correct AFAIK, since I have a 1280x1024 on the left and 1600x1200 on the right.
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2880 1200
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

---

