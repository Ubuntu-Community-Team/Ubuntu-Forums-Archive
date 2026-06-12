---
title: "[SOLVED] Telling Linux to search a specific dir for fonts"
date: 2008-07-31
forum: General Help
---

### Post by FFighter on 2008-07-31
Hi,

Is there a way to tell Linux (or whatever software component is responsible for fonts on Linux) to look into a specific dir for fonts? For example, let's say I have a /home/user/myfancyfonts dir with several ttf fonts. This dir is also shared with a Windows machine through the smb protocol. Besides the default /home/user/.font dir, I would like to tell the enviroment to also search this path for fonts and load them into memory. Is that possible?

Thanks in advance!

---

### Post by kerry_s on 2008-07-31
put the path in xorg.conf.

eample:

```
Section "Files"
**        FontPath        "/other/path/to/look"**
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

---

