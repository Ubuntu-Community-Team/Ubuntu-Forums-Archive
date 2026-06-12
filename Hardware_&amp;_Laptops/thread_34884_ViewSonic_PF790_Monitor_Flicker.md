---
title: "ViewSonic PF790 Monitor Flicker"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by toran on 2005-05-16
Hello. I'm having a problem, when there is much activity on my screen (especially with 3d things such as screen savers) my monitor flickers a lot. I believe I may have my xorg.conf file set up incorrectly. Could you guys take a look at my set up and help me?

Note: I am trying to use this at 1600x1200 resolution

Monitor: 
[img]http://img.ferra.ru/catalog/img/items/4430_00.jpg[/img]
ViewSonic 19" CRT, PF790 Professional Series

(from manufacturer website, [link](http://www.viewsonic.com/support/desktopdisplays/crtmonitors/proseries/pf790/) )
1600x1200 maximum resolution @ 77Hz
1280x1024 @ 89Hz
1024x768 @ 118Hz
800x600 @ 148Hz

My xorg configuration:

[http://pastebin.ca/raw/11936](http://pastebin.ca/raw/11936)

excerpt from it:
```

Section "Monitor"
	Identifier	"PF790-2"
	Option		"DPMS"
	HorizSync	31.5-97
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Monitor		"PF790-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
EndSection

```

Thanks for any help!

toran

---

