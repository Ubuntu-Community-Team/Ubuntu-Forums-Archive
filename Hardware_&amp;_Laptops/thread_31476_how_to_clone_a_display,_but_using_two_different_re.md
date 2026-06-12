---
title: "how to clone a display, but using two different resolutions?"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by phen on 2005-05-03
Hello!

I browsed through several forums, to get my external LCD screen up and running. Now it runs flawlessly, but in dual head mode. What i would like to have is a simple clone of my laptop display, but with a different resolution (laptop: 14", external: 19" :-).

I hesitate to start trying again by myself, because i wasn't successful at all :-(

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 "Screen0" 0 0
	Screen 1 "Screen1" LeftOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Thanks for all ideas!

kai

---

