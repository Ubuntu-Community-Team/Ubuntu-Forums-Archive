---
title: "Configure Tilt Wheel Mouse"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by Paradoxdruid on 2006-07-28
I've successfully got evdev running with my Logitech MediaPlay mouse, and using xev I cna tell that the tilt left button is 11 and tilt right is 12.

How can I configure konqueror and firefox to recognize the tilt?

I used this guide to get my mouse buttons recognized:  [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894), so now my mouse section of my xorg.conf looks like this:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9" #this should be that underlined name from 19-local.rules
EndSection
```

If I add a ZAxis Mapping line to the above, X won't start (and I'm not sure ZAxis mapping is what I want, anyway, but I thought I'd throw that info in).

What do I need to do to configure my tilt wheel?

Thanks for any help or advice.

---

