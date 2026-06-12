---
title: "forward/backward buttons in 7.10 on IBM T40"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by john8520 on 2007-11-07
I just installed Ubuntu 7.10 on my ThinkPad T40 after getting totally fed up with windows XP.  (reinstall drivers because I plug a mouse into a new USB port? COME ON!). And all in all I'm very happy with how ubuntu has turned out so far, my wifi worked right away as did speedstep and power management. I even found how to use the trackpoint for scrolling! 

However, what I have not been able to find out how to do is use the backwards/forwards keys in firefox. According to the keyboard shortcuts application, the forward button is 0xea and the backwards button is 0xe9. Keyboard shortcuts allows me to set these keys for audio players, but not for web browsers, as far as I can tell.

Any ideas?

John

---

### Post by Tinsley614 on 2007-11-07
Ditto me, I'm running a T60 and would like the use of those buttons as well, but I have been unsuccessful at getting the trackpoint scrolling to work. If you could tell me what it was that you did, that'd be great. Thanks in advance.

---

### Post by john8520 on 2007-11-07
Oh man, getting scrolling to work is easy. In xorg.conf, under the "Configured Mouse" section (Under a "Section "InputDevice"") add:

```

	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButton"	"2"

```

Right above EndSection.

Now restart X and you can hold down the blue button and scroll up and down, right/left doesn't seem to work though,

---

### Post by phen on 2007-11-17
the forward backward keys would be interesting for me, too!

therefore: bump :)

---

### Post by john8520 on 2007-11-17
I've yet to find anything good... if I do I'll post back...

---

