---
title: "Error: Failed to construct test pipeline for 'Video for Linux (v4l)"
date: 2005-12-01
forum: General Help
---

### Post by kerinin on 2005-12-01
i'm working on a fresh install of breezy (AMD64), and i'm trying to get my webcam working.  from what i can tell the driver is working ok (using spca5xx), but v4l seems to be broken.  

The error in the tiitle is created when i go to Settings > Preferences > Multimedia Systems Selector and try to test the v4l input.  

I've added a line to my xorg.conf file to load the v4l moules, here's the relevant info:
```
Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"v4l"
EndSection
```

does anyone have any idea why this isn't working?  is this a problem with v4l, or is this a problem with my webcam which is preventing v4l from working?  suggestions on what to do now?

thanks!

---

