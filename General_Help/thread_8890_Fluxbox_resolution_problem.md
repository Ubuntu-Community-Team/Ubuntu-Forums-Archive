---
title: "Fluxbox resolution problem"
date: 2004-12-22
forum: General Help
---

### Post by Swab on 2004-12-22
I am having a problem with Fluxbox.  When I login it uses 1600x1200 resolution.  Now I am able to change resolution by using Ctrl+Alt and + or - but my desktop workspace size seems to remain unchanged.  So I end up with say 800x600 resolution but a desktop size of 1600x1200.  I am able to move my mouse around and scroll around the screen.  What am I missing here?

Here is my XF86Config file, not sure if this has anything to do with it.

```
Section "Monitor"
	Identifier	"PF775"
	HorizSync	30-97
	VertRefresh	50-180
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 Pro Ultra (TF)"
	Monitor		"PF775"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

---

### Post by InvIsiBlekID on 2005-05-09
Someone please help, i have the exact same problems, my XF86Config-4 file is almost identical, but i dont have an ATI card.  Thanks in advance!  8)

---

