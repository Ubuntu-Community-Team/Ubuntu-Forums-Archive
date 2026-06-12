---
title: "how can i change resolution"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by lorap on 2005-05-04
i can't change resolution!
it's disabled!
only one possibility choosed by the system.
thanx.
pavel

---

### Post by ignavia on 2005-05-04
Do you have more than one resolution listed in /etc/X11/xorg.conf? During setup, when it asked you to choose your resolutions, did you only choose one?

---

### Post by lorap on 2005-05-04
yes,i see only one resolution in the list and only refresh rate 60hz.
i wasn't asked to choose the resolution when installation.
thanx
pavel

---

### Post by ignavia on 2005-05-04
Change that part of your config file to something like this:

```
        SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
```

If you only have one depth section, it'll let you change res without restarting the desktop.

---

### Post by lorap on 2005-05-04
i've already it written there this way,but the problem's it an only option.
regardless nvidia driver been installed i still can't change resolution...
it's impossible to work this way.warty recognized it very well at a past...

---

