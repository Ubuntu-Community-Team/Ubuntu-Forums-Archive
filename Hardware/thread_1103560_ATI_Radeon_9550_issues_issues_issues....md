---
title: "ATI Radeon 9550 issues issues issues..."
date: 2009-03-22
forum: Hardware
---

### Post by Delliriumy on 2009-03-22
Well at starts ive just switched to linux (had only slight connection with it on my university).

I have some problems with this damn graph card.Ive seen a lot topics about it and still couldnt make it work properly.Now i just feel that ive messed way to much.


<<<fglrxinfo>>>
```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

<<<xorg.konf>>>
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "ati"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "VideoGLOverlay"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection


```

If u need more information , shoot plz :).Im really struggling with it aloooot =/

---

